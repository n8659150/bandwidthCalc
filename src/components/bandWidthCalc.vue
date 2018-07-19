<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "bandWidthCalc",
  data() {
    return {
      msg: "正在测速...",
      time: 10,
      startTime: null,
      endTime: null,
      fileSize: 0,
      result: null
    };
  },
  methods: {
    goMeasure(time) {
      this.startTime = Date.now();
      for (let x = time; x > 0; x--) {
        this.measureBWSimple(time);
      }
    },
    measureBWSimple(time) {
      let xhr = new XMLHttpRequest();
      xhr.onreadystatechange = () => {
        if (xhr.readyState === 4 && xhr.status === 0) {
          this.msg = '无法检测您的带宽，请检查网络连接是否畅通';
        }

        if (xhr.readyState === 4 && xhr.status === 200) {
          if (!this.fileSize) {
            this.fileSize = xhr.responseText.length;
          }
          this.time--;
          if (this.time <= 0) {
            this.endTime = Date.now();

            let speed =
              this.fileSize *
              time /
              ((this.endTime - this.startTime) / 1000) /
              1024;

            this.result =
              speed >= 1000
                ? Math.floor(speed) / 1000 + "MB/s"
                : Math.floor(speed) + "KB/s";

            this.msg = `您的带宽约等于 ${this.result}`;
          }
        } 
      };
      xhr.open(
        "GET",
        "https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Templo_de_Garni%2C_Armenia%2C_2016-10-02%2C_DD_03.jpg/1920px-Templo_de_Garni%2C_Armenia%2C_2016-10-02%2C_DD_03.jpg",
        true
      );
      xhr.send();
    }
  },
  mounted() {
    this.goMeasure(this.time);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
