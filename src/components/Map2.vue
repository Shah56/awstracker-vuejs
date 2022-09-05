<template>
  <div class="q-pa-md">
    <div id="map" style="width: 100%;height: 40vw"></div>
  </div>
</template>

<script>
    import maplibregl from 'maplibre-gl'
    import { Auth} from 'aws-amplify'
    import { Signer } from "@aws-amplify/core";
    import awsconfig from '../aws-exports'

    export default {
        name: 'MapPane',
        data() {
            return {
                credentials: null,
            }
        },
        mounted: async function () {
            this.credentials = await Auth.currentCredentials()
            this.mapCreate();
        },
        methods: {
            mapCreate: function() {
                const map = new maplibregl.Map({
                    container: 'map',
                    style: 'TrackerMap',
                    center: [139.7648, 35.6794],
                    zoom: 15,
                    bearing: 64.8,
                    pitch: 60,
                    hash: true,
                    transformRequest: this.transformRequest,
                });

                map.addControl(new maplibregl.NavigationControl());
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
        }
    }
</script>