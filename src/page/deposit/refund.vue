<template>
    <div>
        <headerNav title="退款申请"/>
        <div class="join">
            <form action="" method="post">
                <label>玩家微信号</label>
                <div>
                    <input type="text" placeholder="玩家微信号">
                </div>
                <label>收款方微信号</label>
                <div>
                    <input type="text" placeholder="收款方微信号">
                </div>
                <label>押金金额</label>
                <div>
                    <input type="text" placeholder="押金金额">
                </div>
                <label>转账凭据</label>
                <div>
                </div>
                <div class="person fl">
                    <div id="preview">
                        <img id="imghead" src="../../assets/images/head_180.jpg">
                    </div>
                    <input type="file" @change="previewImage($event)" class="upload" id="file">
                    <label for="file">
                        <svg xmlns="http://www.w3.org/2000/svg" width="15" height="12" viewBox="0 0 20 17">
                            <path d="M10 0l-5.2 4.9h3.3v5.1h3.8v-5.1h3.3l-5.2-4.9zm9.3 11.5l-3.2-2.1h-2l3.4 2.6h-3.5c-.1 0-.2.1-.2.1l-.8 2.3h-6l-.8-2.2c-.1-.1-.1-.2-.2-.2h-3.6l3.4-2.6h-2l-3.2 2.1c-.4.3-.7 1-.6 1.5l.6 3.1c.1.5.7.9 1.2.9h16.3c.6 0 1.1-.4 1.3-.9l.6-3.1c.1-.5-.2-1.2-.7-1.5z"></path>
                        </svg>
                        <span>上传转账凭据</span></label>
                </div>

                <div class="qrcode fr">
                    <div id="preview1">
                        <img id="imghead1" src="../../assets/images/head_180.jpg">
                    </div>
                    <input type="file" @change="previewImage1($event)" id="file1" class="upload">
                    <label for="file1">
                        <svg xmlns="http://www.w3.org/2000/svg" width="15" height="12" viewBox="0 0 20 17">
                            <path d="M10 0l-5.2 4.9h3.3v5.1h3.8v-5.1h3.3l-5.2-4.9zm9.3 11.5l-3.2-2.1h-2l3.4 2.6h-3.5c-.1 0-.2.1-.2.1l-.8 2.3h-6l-.8-2.2c-.1-.1-.1-.2-.2-.2h-3.6l3.4-2.6h-2l-3.2 2.1c-.4.3-.7 1-.6 1.5l.6 3.1c.1.5.7.9 1.2.9h16.3c.6 0 1.1-.4 1.3-.9l.6-3.1c.1-.5-.2-1.2-.7-1.5z"></path>
                        </svg>
                        <span>上传转账凭据</span></label>
                </div>
                <input type="button" @click="submitData" value="提交审核">
            </form>
        </div>


        <navigate />
    </div>
</template>

<script>
    import '../../assets/style/main.css';
    import navigate from '../../components/footer/navigate.vue'

    export default {
        components:{
            navigate
        },
        data() {
            return {

            }
        },
        methods: {
            submitData() {
                alert("11");
            },
            previewImage(event) {
                let file = event.currentTarget;
                var MAXWIDTH = 260;
                var MAXHEIGHT = 180;
                var div = document.getElementById('preview');
                if (file.files && file.files[0]) {
                    div.innerHTML = '<img id=imghead>';
                    var img = document.getElementById('imghead');
                    var that = this;
                    img.onload = function () {
                        var rect = that.clacImgZoomParam(MAXWIDTH, MAXHEIGHT, img.offsetWidth, img.offsetHeight);
                        img.width = rect.width;
                        img.height = rect.height;
                        img.style.marginTop = rect.top + 'px';
                    }
                    var reader = new FileReader();
                    reader.onload = function (evt) {
                        img.src = evt.target.result;
                    }
                    reader.readAsDataURL(file.files[0]);
                }
                else {
                    var sFilter = 'filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(sizingMethod=scale,src="';
                    file.select();
                    var src = document.selection.createRange().text;
                    div.innerHTML = '<img id=imghead>';
                    var img = document.getElementById('imghead');
                    img.filters.item('DXImageTransform.Microsoft.AlphaImageLoader').src = src;
                    var rect = clacImgZoomParam(MAXWIDTH, MAXHEIGHT, img.offsetWidth, img.offsetHeight);
                    status = ('rect:' + rect.top + ',' + rect.left + ',' + rect.width + ',' + rect.height);
                    div.innerHTML = "<div id=divhead style='width:" + rect.width + "px;height:" + rect.height + "px;margin-top:" + rect.top + "px;" + sFilter + src + "\"'></div>";
                }
            },
            previewImage1(event) {
                let file = event.currentTarget;
                console.log(1);
                let MAXWIDTH = 260;
                let MAXHEIGHT = 180;
                let div = document.getElementById('preview1');
                if (file.files && file.files[0]) {
                    div.innerHTML = '<img id=imghead1>';
                    let img = document.getElementById('imghead1');
                    var that = this;
                    img.onload = function () {
                        let rect = that.clacImgZoomParam(MAXWIDTH, MAXHEIGHT, img.offsetWidth, img.offsetHeight);
                        img.width = rect.width;
                        img.height = rect.height;
                        img.style.marginTop = rect.top + 'px';
                    }
                    let reader = new FileReader();
                    reader.onload = function (evt) {
                        img.src = evt.target.result;
                    }
                    reader.readAsDataURL(file.files[0]);
                }
                else {
                    let sFilter = 'filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(sizingMethod=scale,src="';
                    file.select();
                    let src = document.selection.createRange().text;
                    div.innerHTML = '<img id=imghead1>';
                    let img = document.getElementById('imghead1');
                    img.filters.item('DXImageTransform.Microsoft.AlphaImageLoader').src = src;
                    let rect = this.clacImgZoomParam(MAXWIDTH, MAXHEIGHT, img.offsetWidth, img.offsetHeight);
                    status = ('rect:' + rect.top + ',' + rect.left + ',' + rect.width + ',' + rect.height);
                    div.innerHTML = "<div id=divhead1 style='width:" + rect.width + "px;height:" + rect.height + "px;margin-top:" + rect.top + "px;" + sFilter + src + "\"'></div>";
                }
            },
            clacImgZoomParam(maxWidth, maxHeight, width, height) {
                var param = {top: 0, left: 0, width: width, height: height};
                if (width > maxWidth || height > maxHeight) {
                    rateWidth = width / maxWidth;
                    rateHeight = height / maxHeight;
                    if (rateWidth > rateHeight) {
                        param.width = maxWidth;
                        param.height = Math.round(height / rateWidth);
                    } else {
                        param.width = Math.round(width / rateHeight);
                        param.height = maxHeight;
                    }
                }
                param.left = Math.round((maxWidth - param.width) / 2);
                param.top = Math.round((maxHeight - param.height) / 2);
                return param;
            }
        }
    }
</script>
<style>

</style>


