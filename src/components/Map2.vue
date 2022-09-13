<template>
  <div class="q-pa-md">
    <div id="map" style="width: 100%;height: 40vw"></div>
  </div>
</template>

<script>
    import maplibregl from 'maplibre-gl'
    import { Auth} from 'aws-amplify'
    import { Signer } from "@aws-amplify/core";
    import awsconfig from '../../aws-exports'
    import location from "aws-sdk/clients/location";

    export default {
        name: 'MapPane',
        data() {
            return {
                credentials: null,
                map: null,
            }
        },
        mounted: async function () {
            this.credentials = await Auth.currentCredentials()
            this.locationService = new location({
              credentials: this.credentials,
              region: awsconfig.aws_project_region,
            });
            
            
            console.log("Calling get Positions")
            let trackerInfo = await this.getPositions();
            console.log("Calling Render Map")
            await this.mapCreate(trackerInfo[0][0].Position[0],trackerInfo[0][0].Position[1]);
            console.log("Render Map Call Complete")
            this.pointOnCircle(trackerInfo[0][0].Position[0],trackerInfo[0][0].Position[1],trackerInfo[0][0].DeviceId,trackerInfo[0][0].SampleTime);
        },
        methods: {
            mapCreate: function(lng,lat) {
                var vm = this;
                vm.map = new maplibregl.Map({
                    container: 'map',
                    style: 'TrackerMap',
                    center: [lng,lat],
                    zoom: 15,
                    bearing: 64.8,
                    pitch: 0,
                    hash: true,
                    transformRequest: this.transformRequest,
                });

                vm.map.addControl(new maplibregl.NavigationControl());
            },
            transformRequest: function (url, resourceType) {
                if (resourceType === 'Style' && !url.includes('://')) {
                    url = `https://maps.geo.${awsconfig.aws_project_region}.amazonaws.com/maps/v0/maps/${url}/style-descriptor`
                }
                if (url.includes('amazonaws.com')) {
                    return {
                        url: Signer.signUrl(url, {
                            access_key: this.credentials.accessKeyId,
                            secret_key: this.credentials.secretAccessKey,
                            session_token: this.credentials.sessionToken,
                        }),
                    }
                }
                return { url }
            },
            batchGetDevicePosition(params) {
                var vm = this;
                return new Promise(function(resolve, reject) {
                    vm.locationService.batchGetDevicePosition(params, function(
                        err,
                        data
                    ) {
                        if (err) {
                        console.log(err, err.stack);
                        reject([]);
                        } else {
                        resolve(data.DevicePositions)
                        }
                    })
                })
            },
            async getPositions() {
            console.log("Called get Positions")
                let devicePositionAll = []
                var params = {
                    DeviceIds: ["7028534685"],
                    TrackerName: "explore.tracker",
                };
                   
                let bathPos = await this.batchGetDevicePosition(params)
                devicePositionAll.push(bathPos)
                console.log("Retrieved coords:" + bathPos)        
                console.log(devicePositionAll)
                return devicePositionAll;       
            
            },
            async pointOnCircle(lng,lat,deviceId,sampleTime) {
                let name = deviceId
                let vm = this
                let color = "#ff0000"
                console.log("called point on circle with info: " + lng + lat + deviceId + sampleTime)
                //if (this.map.getLayer(name)) this.map.removeLayer(name);
                //if (this.map.getSource(name)) this.map.removeSource(name);
                console.log("calling add source")
                vm.map.on('load', function () {
                    vm.map.addSource(name, {
                    type: 'geojson',
                    data: {
                    type: "Point",
                    coordinates: [lng, lat]
                    }
                    });      
 
                });
               
                // Add red if timeDiff is X
                //if (mm >= 10) color = '#ff0000'
                console.log("calling add layer")
                vm.map.on('load', function () {
                    vm.map.addLayer({
                    'id': name,
                    'source': name,
                    'type': 'circle',
                    'paint': {
                    'circle-radius': 12,
                    'circle-color': color
                    }
                    });   
                });
                   

                vm.map.on('click',  function () {
                    vm.popUps[name]
                    .setLngLat([lng,lat])
                    .setHTML(deviceId + " - " + sampleTime)
                    .addTo(vm.map)
                });

                // Change the cursor to a pointer when the mouse is over the states layer.
                vm.map.on('mouseenter',  function () {
                    vm.map.getCanvas().style.cursor = 'pointer';
                });
                
                // Change it back to a pointer when it leaves.
                vm.map.on('mouseleave',  function () {
                    vm.map.getCanvas().style.cursor = '';
                });

            },
        }
    }
</script>