<template>
  <div>
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
      result: null,
      imgSrc:'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Templo_de_Garni%2C_Armenia%2C_2016-10-02%2C_DD_03.jpg/1920px-Templo_de_Garni%2C_Armenia%2C_2016-10-02%2C_DD_03.jpg?v='
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
          this.msg = '无法检测您的下载速度，请检查网络连接是否畅通';
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

            this.msg = `您的下载速度约等于 ${this.result}`;
          }
        } 
      };
      // 解决浏览器缓存图片的问题
      this.imgSrc = `${this.imgSrc}${Math.random().toString().slice(-6)}`;
      xhr.open(
        "GET",
        this.imgSrc,
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
h1{
  font-weight: normal;
}
</style>
