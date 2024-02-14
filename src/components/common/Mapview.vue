<template>
    <div id="mapview"></div>
</template>

<script>
    import { loadModules } from 'esri-loader';

    const option = {
        url: ' https://js.arcgis.com/4.28/init.js',
        css: 'https://js.arcgis.com/4.28/esri/themes/light/main.css',
    };

    export default {
        name: 'MapView',
        components: {},
        mounted: function () {
            this._createMapView();
        },
        methods: {
            async _createMapView() {
                const [Map, MapView] = await loadModules(
                    ['esri/Map', 'esri/views/MapView'],
                    option
                );

                const map = new Map({
                    basemap: 'topo-vector',
                });

                const view = new MapView({
                    container: 'mapview',
                    map: map,
                    zoom: 10,
                    center: [107.239398, 34.369392],
                });

                view.ui.components = [];
                console.log(view);
            }
        }
    };
</script>

<style>
    #mapview {
        position: relative;
        width: 100%;
        height: 100%;
    }
</style>