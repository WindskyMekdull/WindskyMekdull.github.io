---
layout: article
---

## 历史上的今天

<p id='todinhis'>A F**king Error F**king appears</p>

<script>
  let today = new Date();
  let path = ''
  
  if (today.getMonth() < 9) {
    path += '0'
  }
  path += `${(today.getMonth() + 1)}`

  if (today.getDate() < 10) {
    path += '0'
  }
  path += `${today.getDate()}`
  
  fetch(`https://panda-ghost.github.io/todayinhistory/${path}.json`)
    .then((response) => response.json())
    .then((data) => {
      let event = data[Math.floor(today.getFullYear()%data.length)];
      let inner = `${event.year}年的今天，${event.title.slice(event.title.indexOf(':') + 1)}`;
      document.getElementById('todinhis').innerHTML=inner
    });
</script>
