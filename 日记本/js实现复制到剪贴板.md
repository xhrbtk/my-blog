## js实现复制到剪贴板

```
const copyText = ( link) => {
    console.log('link-----', link)
    let share = document.createElement('p')
    share.id = 'shareLink'
    document.body.appendChild(share)
    shareLink.innerText = link
    shareLink.style = 'position:fixed;bottom:0;z-index:-1000;'
    setTimeout(() => {
      let shareLink = document.getElementById('shareLink')
      let text = shareLink.innerText
      let oInput = document.createElement('input')
      oInput.value = text
      document.body.appendChild(oInput);
      oInput.select()
      document.execCommand("Copy")
      oInput.id = 'oInput'
      oInput.style.display = 'none'
      JSB.UI.toast(i18n.t('shareSetting.toast1'))
      oInput.remove()
      shareLink.remove()
    })
  }
```