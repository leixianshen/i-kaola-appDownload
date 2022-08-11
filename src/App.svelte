<script>
import { onMount } from 'svelte';
import axios from 'axios'

// 文件打开路径
let dowmloadUrl=""
//判断是否是安卓  默认是安卓
let isAndroid=true

// 下载
const dowmloadApp=()=>{
    window.open(dowmloadUrl);
}


// 判断环境, 获取地址
onMount(()=>{
    const u=navigator.userAgent;

// 是否是IOS
    if(!!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/)){
        isAndroid=false
        dowmloadUrl='itms-services://?action=download-manifest&url=https://i8-public.oss-cn-shanghai.aliyuncs.com/app/tianyue.plist'
    }else{
        dowmloadUrl='https://i8-public.oss-cn-shanghai.aliyuncs.com/app/tianyue.apk'
    }

    // axios.post('http://192.168.93.47:8888/?fn=GetVersionList',{},{headers:{command:'CPEC.Apps.Foundation.General.VersionServicceProxy.GetVersionList',token:'exam',

    // }}).then((res)=>{
    //     console.log(res,'11111111111111111')
    // })

})



</script>

<main>
 <div class="userTest">
    <img src={'/appBackground.png'} alt='下载页背景图片' width="100%" class="bgImg"/>
    <div class="AppBtnClass" on:click={dowmloadApp}>
        <img src={'/appBtn.png'} alt='下载按钮' width="100%"/>
    </div>
 </div>
</main>

<style>
 
</style>
