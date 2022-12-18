<script context="module" lang="ts">
    const key = "dataGeoSaveApp"

    export let data = []
    export function LoadSavedData(){
        let savedData = window.localStorage.getItem(key)
        if(savedData != null){
            data = JSON.parse(savedData)
            data = data
        }
        console.log(data)
    }

    function SaveData(){
        window.localStorage.setItem(key, JSON.stringify(data));
    }

    export function AddElementToData(position){
        data.push({
            dateKey: new Date().toJSON(),
            latitude: position.coords.latitude,
            longitude: position.coords.longitude,
            deviceDirection: position.coords.heading
        })
        data = data;
        SaveData();
    }

</script>