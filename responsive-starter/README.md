# Vue 3 - TypeScript - Responsive Composition API


# Outline

-   Getting Started
    -   Build an application to automatically detect mobile or web
    -   Show different pages according to the device
-   Overview of Tasks and Goals using Composition API
    -   Use Composition API to monitor screen size changes
    -   Use reactive to monitor browser and device size
    -   Use reactive state to monitor sizes and return if it’s mobile or larger
    -   Add Event Listener to monitor resize changes
-   Live Coding
    -   Cloning responsive GitHub starter and final project
    -   Create Composable useMonitorSize function
    -   Run the Application and resize the browser window to watch the appropriate Mobile or Web page displayed
-   Summary
    -   You learned to use Composition API to monitor screen size changes
    -   You used the Composable function to monitor screen size changes
    -   You used the reactive state to monitor sizes and return if it’s mobile or larger
    -   You used Event Listener to monitor resize changes
    -   Thank you

----------

# Composition API Exercise

1.  Live Coding Starter Project
    
    1.  Clone the **responsive** project from [GitHub](https://github.com/JediPixels/responsive)
    2.  Open the **responsive-starter** project folder
2.  Creating Composables
    
    1.  Create the **composables** folder under the **src** folder
    2.  Create the monitor-size.ts file
    3.  Add export **useMonitorSize** function
    4.  Declare **sizes** with **reactive** state containing the **browserWidth**, **deviceWidth**, and **isMobile** objects
    5.  Declare the **broserResized** function to reactively monitor browser window changes
    6.  Declare the **isMobile** function to determine if window size breakpoint is mobile
    7.  Declare **onMounted** function to add window Event Listener resize property tied to the **browserResized** function
    8.  Declare **onUnmounted** function to remove window Event Listener
    9.  Add the **return** to expose the **sizes** state using the **toRefs** to convert **reactive** object to **refs**
    
    ```tsx
    import { onMounted, onUnmounted, reactive, toRefs } from "vue";
    
    export function useMonitorSize() {
        const sizes = reactive({
            browserWidth: window.innerWidth,
            deviceWidth: screen.width,
            isMobile: false
        })
    
        
        const browserResized = () => {
            sizes.browserWidth = window.innerWidth
            sizes.deviceWidth = screen.width
            sizes.isMobile = isMobile()
        }
    
        const isMobile = () => {
            return window.innerWidth <= 600 ? true : false
        }
    
        onMounted(() => {
            window.addEventListener('resize', browserResized)
        })
    
        onUnmounted(() => {
            window.removeEventListener('resize', browserResized)
        })
    
        return {
            ...toRefs(sizes)
        }
    }
    
    ```
    
3.  Modifying the Responsive page by adding Composition API
    
    1.  Open the **responsive.vue** page and add the **useMonitorSize** Composition API Function declaration
    2.  Modify the h2 tags and add the **sizes.browserWidth**, and **sizes.deviceWidth** showing the current browser width and device width
    3.  Add **v-if** directive to the Mobile and **v-else** directive to the Web components to show the appropriate page depending on browser width
    
    ```tsx
    <script setup lang="ts">
    import { useMonitorSize } from '../composables/monitor-size';
    import Mobile from './mobile.vue';
    import Web from './web.vue';
    
    const sizes = useMonitorSize();
    </script>
    
    <template>
        <h2>{{ sizes.browserWidth }} pixels: Browser </h2>
        <h2>{{ sizes.deviceWidth }} pixels: Device</h2>
      
        <Mobile v-if="sizes.isMobile.value" />
        <Web v-else />
    </template>
    
    ```
    
    1.  Run the Application and resize the browser window to watch the appropriate Mobile or Web page displayed

----------

# Video

[![Watch the video](https://img.youtube.com/vi/hBvkABCIjJo/maxresdefault.jpg)](https://youtu.be/hBvkABCIjJo)

----------
