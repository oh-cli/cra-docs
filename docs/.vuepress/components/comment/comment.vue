<template>
  <div class="gitalk-container">
    <div id="gitalk-container"></div>
  </div>
</template>

<script>
export default {
  name: "comment",
  data() {
    return {};
  },
  mounted() {
    let body = document.querySelector(".gitalk-container");
    let script = document.createElement("script");
    script.src = "https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js";
    body.appendChild(script);
    script.onload = () => {
      const commentConfig = {
        clientID: "06d8ac6a043dbf4e4b90",
        clientSecret: "99f78d789eff94ddc5c59aa7485104be7f9e8f23",
        repo: "cra-docs",
        owner: "fyz1994",
        // 这里接受一个数组，可以添加多个管理员，可以是你自己
        admin: ["fyz1994"],
        // id 用于当前页面的唯一标识，一般来讲 pathname 足够了，
        // 但是如果你的 pathname 超过 50 个字符，GitHub 将不会成功创建 issue，此情况可以考虑给每个页面生成 hash 值的方法.
        id: document.title.replace(/\s\|\sbs-cra|《|》/g, ""),
        distractionFreeMode: false
      };
      const gitalk = new Gitalk(commentConfig);
      gitalk.render("gitalk-container");
    };
  }
};
</script>

<style>
@import url("https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css");
</style>
