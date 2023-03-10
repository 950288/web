<template>
  <div class="content is-large">
    <h2>width: 1024px</h2>
    <p>
      2022-12-25 22:05:14
    </p>
    <div id="chart">

      <!-- iGEMGotool look1 start-->
      <h1>iGEMGoTool （<a target="_blank" rel="noopener noreferrer nofollow"
          href="https://github.com/950288/iGEMGoTool/blob/main/README_zh.md">简体中文</a>）🛠️</h1>
      <p>iGEMGoTool is an online collaborative wiki content editor that enables complete separation of wiki code
        writing🧑‍💻 and content filling ✍️ with high adaptability and extremely concise operability 🦾, which can
        greatly improve wiki development efficiency 🥰.</p>
      <h2>Introduction for Users (developing)🧑‍💼</h2>
      <p>iGEMGoTool is a user-friendly online editor 🧰 that allows iGEM teams to easily edit wikis. it provides a
        simple interface for editing wiki content pages. And only one person from the whole team needs to install it to
        enable collaborative editing for the whole team. With iGEMGoTool, wiki content editors can focus on quality
        content without having to think about the technical details of HTML and CSS.</p>
      <p>To use iGEMGoTool, follow these steps:</p>
      <ul>
        <li>
          <p>Download the latest version of the <code>iGEMGoTool</code> zip archive, put the Unziped
            <code>iGEMGoTool</code> folder into the root directory of your project.</p>
        </li>
        <li>
          <p>Insert the following special tag into your <code>.html</code> file or other custom file type for each
            section that you want to edit: <code>&lt;!-- iGEMGoTool {{ name }} start--&gt;</code>. Replace
            <code>{{ name }}</code> with the The custom name for this section.(Note: A page can contain multiple tags and
            each tag corresponds to a section that can be edited individually.)</p>
        </li>
      </ul>
      <pre><code>&lt;div&gt; &lt;!-- iGEMGotool test1 start--&gt; &lt;/div&gt;</code></pre>
      <ul>
        <li>
          <p>Double-click the iGEMGoTool executable to run the tool. Then you can see to generated URL in the Console
            like below. You can edit you page in the browser through the generated URL, iGEMGoTool also supports
            collaborative editing within a LAN (e.g. personal hotspot, campus network, etc.), where team members within
            the same LAN can access the editing page via the second link.</p>
        </li>
      </ul>
      <p><code>Server started on port 8080 Local: http://127.0.0.1:8080/ Network: http://192.168.Xx.xx:8080/</code></p>
      <ul>
        <li>
          <p>For advanced usage, you can deploy iGEMGoTool to a personal server and open ports for the service without
            worrying about LAN restrictions</p>
        </li>
      </ul>
      <p>we also provide configuration file, <code>config.json</code>, which will be automatically generated upon the
        first run of the application. It allows the user to customize certain parameters such as the directory
        containing the pages to be modified, the directory to store the edited pages data, the port to be used, the tag
        to be scanned for insertion, and the file types to be scanned. The default values for these parameters can be
        seen in the example configuration file below:</p>
      <p>
        <code>{ // Directory containing the page to be modified (e.g. "D:\\github\\web\\src\\pages") "ScanDirectory": "..\\", // Directory to store the edited page (e.g. "D:\\github\\web\\src\\iGEMGotoolData") "StoreDirectory": "..\\iGEMGotoolData", //Port to be used "Port": 8080, //the tag to be scan and incert content (e.g. "iGEMGotool"), //which be automatically converted to &lt;!-- iGEMGotool {{ name }} start--&gt; "incert tag":"iGEMGotool", //file type to be scan (e.g. [".html",....]) "file type":[".html",".vue"] }</code>
      </p>
      <h2>Project Building Guide 🧑‍💻</h2>
      <p>The following is for developers wishing to make improvements to the tool, but if you just want to do basic
        usage, no further reading is required!</p>
      <p>iGEMGoTool is developed using a modern stack that includes Vue 3 and Go. The front-end is implemented using Vue
        3 and Typescript, and it is built using the Vite build tool. The back-end is implemented using Go and provides a
        RESTful API for the front-end to interact with.</p>
      <p>To set up the development environment for iGEMGoTool, you will need to have <a target="_blank"
          rel="noopener noreferrer nofollow" href="https://nodejs.org/">Node.js</a> and <a target="_blank"
          rel="noopener noreferrer nofollow" href="https://golang.org/">Go</a> installed on your system. Then, follow
        these steps:</p>
      <ul>
        <li>
          <p>Clone this repository and navigate to the root directory.</p>
        </li>
        <li>
          <p>Run <code>npm install</code> to install the required dependencies for the front-end.</p>
        </li>
      </ul>
      <p>To start the development for the front-end, run <code>npm run dev</code>. To build the front-end for
        production, run <code>npm run build-web</code>.</p>
      <p>All cose for back-end is under the <code>GoTool</code> directory. To start the development for the back-end,
        run <code>go run GoTool/serve.go</code>. To build the back-end, run <code>npm run build-go</code>.</p>
      <p>To build both the front-end and back-end for production, run <code>npm run build-all</code>. The target program
        generated by the compilation is under the dist folder</p>
      <h2>Working Principle 📝</h2>
      <p>The working principle of iGEMGoTool can be summarized in the following diagram:</p>
      <p>The front-end WebEditor sends HTTP requests to the back-end to retrieve and update the edited content. The
        backend reads and writes automatically generated data files in real time and synchronizes the changes to the
        wiki code.</p>
      <h2>Technology Stack 🛠️</h2>
      <ul>
        <li>
          <p>Front-end: Vue 3, TypeScript, Vite, tiptap</p>
        </li>
        <li>
          <p>Back-end: Go</p>
        </li>
        <li>
          <p>Build tool: Vite, go build</p>
        </li>
      </ul><!-- iGEMGotool look1 end-->
      <apexchart v-if="renderComponent" type="line" height="350" :options="chartOptions" :series="series"></apexchart>

      <!-- iGEMGotool look1 start-->
      <apexchart v-if="renderComponent" type="area" height="350" :options="chartOptions0" :series="series0"></apexchart>
      <apexchart v-if="renderComponent" type="line" height="350" :options="chartOptions" :series="series"></apexchart>
      <apexchart v-if="renderComponent" type="area" height="350" :options="chartOptions0" :series="series0"></apexchart>
    </div>
  </div>
</template>
<script setup lang="ts">
import apexchart from 'vue3-apexcharts';
import { themeMode } from "@/main";
import { nextTick, watch, ref } from 'vue';
const renderComponent = ref(true);
const name = "name";

console.log(themeMode.value);
let series = [{
  data: [34, 44, 54, 21, 12, 43, 33, 23, 66, 66, 58]
}];
let chartOptions = {
  chart: {
    type: 'line',
    height: 350
  },
  stroke: {
    curve: 'stepline',
  },
  dataLabels: {
    enabled: false
  },
  title: {
    text: 'Stepline Chart',
    align: 'left'
  },
  markers: {
    hover: {
      sizeOffset: 4
    }
  },
  theme: {
    mode: themeMode.value,
    palette: 'palette1',
    monochrome: {
      enabled: false,
      color: '#255aee',
      shadeTo: 'light',
      shadeIntensity: 0.65
    },
  },
}
let series0 = [
  {
    name: 'South',
    data: generateDayWiseTimeSeries(new Date('11 Feb 2017 GMT').getTime(), 20, {
      min: 10,
      max: 60
    })
  },
  {
    name: 'North',
    data: generateDayWiseTimeSeries(new Date('11 Feb 2017 GMT').getTime(), 20, {
      min: 10,
      max: 20
    })
  },
  {
    name: 'Central',
    data: generateDayWiseTimeSeries(new Date('11 Feb 2017 GMT').getTime(), 20, {
      min: 10,
      max: 15
    })
  }
]
let chartOptions0 = {
  chart: {
    type: 'area',
    height: 350,
    stacked: true,
    events: {
      selection: function (chart, e) {
        console.log(new Date(e.xaxis.min))
      }
    },
  },
  colors: ['#008FFB', '#00E396', '#CED4DC'],
  dataLabels: {
    enabled: false
  },
  stroke: {
    curve: 'smooth'
  },
  fill: {
    type: 'gradient',
    gradient: {
      opacityFrom: 0.6,
      opacityTo: 0.8,
    }
  },
  legend: {
    position: 'top',
    horizontalAlign: 'left'
  },
  xaxis: {
    type: 'datetime'
  },
  theme: {
    mode: themeMode.value,
    palette: 'palette1',
    monochrome: {
      enabled: false,
      color: '#255aee',
      shadeTo: 'light',
      shadeIntensity: 0.65
    },
  },
}

//rerender chart component on theme change
watch(themeMode, async () => {
  chartOptions0.theme.mode = themeMode.value;
  chartOptions.theme.mode = themeMode.value;
  // Remove MyComponent from the DOM
  renderComponent.value = false;

  // Wait for the change to get flushed to the DOM
  await nextTick();

  // Add the component back in
  renderComponent.value = true;
})
function generateDayWiseTimeSeries(baseval: any, count: any, yrange: any) {
  var i = 0;
  var series = [];
  while (i < count) {
    var x = baseval;
    var y =
      Math.floor(Math.random() * (yrange.max - yrange.min + 1)) + yrange.min;
    series.push([x, y]);
    baseval += 86400000;
    i++;
  }
  return series;
}
</script>
