
<!--Module to save and load data about user localisation-->

<script context="module" lang="ts">
    const key = "dataGeoSaveApp"

    export let data = []

    /**
     * Load Saved Data from the user browser local storage if it exist
     * @constructor
     */
    export function LoadSavedData(){
        let savedData = window.localStorage.getItem(key)
        if(savedData != null){
            data = JSON.parse(savedData)
            data = data
        }
    }

    /**
     * Save Data to the local storage of user browser
     * @constructor
     */
    function SaveData(){
        window.localStorage.setItem(key, JSON.stringify(data));
    }

    /**
     * Add position info to user data and save it
     * @param position
     * @constructor
     */
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