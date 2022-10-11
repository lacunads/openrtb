## Banner Request example
```json
{
	"id": "32f94228-52d3-4bce-be88-5dd1d799ae4f",
	"imp": [{
		"id": "1",
		"tagid": "100040-1002421",
		"bidfloor": 1.00,
		"bidfloorcur": "USD",
		"secure": 0,
		"banner": {
			"w": 320,
			"h": 50,
			"mimes": ["image/png", "image/jpg", "image/gif"]
		}
	}],

	"app": {
		"id": "100461",
		"bundle": "com.midastest.ads",
		"ver": "4050618",
		"publisher": {
			"id": "bd8b25d0-413e-4886-9adf-6a796ff47740"
		}
	},
	"device": {
       "ua": "Mozilla/5.0 (Linux; Android 6.0; vivo Y67 Build/MRA58K; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/100.0.4896.88 Mobile Safari/537.36",
       "ip": "114.124.182.13",
       "geo": {
         "country": "ID"
        },
		"devicetype": 4,
		"make": "WIKO",
		"model": "samsung-sm-g900a",
		"os": "android",
		"osv": "5.1.1",
		"language": "en",
		"carrier": "310410",
		"connectiontype": 7,
		"ifa": "5731b4c8-7cc1-4a09-bb77-24f237d93a66",
		"didsha1": "ecae9042f3e549a4fd1af27a1ed38b5f682fa3ca",
		"didmd5": "c98de3c3706ae57c89f97c0778c8121d",
		"dpidsha1": "a07713adea29cd23fd10a2e81a4fb07e23e00fb7",
		"dpidmd5": "af4935679d392191157f687f48907492"
	},
	"at": 1,
	"tmax": 2000
}
```

## Banner Response Example
```json
{
    "id": "32f94228-52d3-4bce-be88-5dd1d799ae4f",
    "bidid": "a1271eca-efa2-4f9f-8904-a853afec1289",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "a1271eca-efa2-4f9f-8904-a853afec1289",
                    "impid": "1",
                    "price": 118.0806,
                    "nurl": "https://midas-tracker-test.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa8c3eb6cb3763be39af447238100277632423c9c212f3987802acb093fa8f226d2beb00ad9aa5d901a36db98e81c1c0f1639ad363decc476977f6ba1dcb36318671a7a606d34961563c37535b94719f7eb4a8d53d8b3c80d002386ea6227bc2e50cdbcaa0c40a29bee9ef33b63c3f56ae4c59790d02b2be9ce6be9598e84f92c0efb7e9fdcf311fb0326d959dbd306031f78ae6a4a34675ad8bb6e84571c015638463b14fab8eded30cabefcf16c758eac517853709909da5be52230975657723bd0182b8eb7e92423a55066d07ab9c25a2c38cb0df2af9462c41155773054912137f7f508187acdfde64036bbcc7108237648df4168089d1ce5c8bae76768ae1f5a7cbda8f78a3c788123653da1a5f9294f7f410ac5a440063a7a62443efae33253b0e2bb16ed36a35b8720a1a75cd3a053a8f6415a00ecb94de70f89dff8f1e9dd5c1317a91c63f186f6e20d346da0aa4bbb9699eac716e961ac71a8048f0ad68c64b5e6ef9b3fec4e7969facea589f05d3fd1e9db885bcfea115dd393addc945f6de28f8ee1c2706e225370fc925762ef0ecb7317c28478b40b09f7b7611fc975cb19ea99226b086ca9c98895c8b86f12fa79b8086c1a3cff9f768f9b729c65121107709120f269c2ea863bda8797e77a98e3f177128fcbb4f46da9addbb1da7ef21f9aef6d0b9b1f4890d3cf764037f056e83dc7ed96a55cfab626fcf5903476d16ece901558cb0c2edc5a43cc57e4c95218c9d01e2e816d005a4f7e&auction_price=${AUCTION_PRICE}&sid=__SID__",
                    "adm":"<a class=\"_rnd_ad_128263\" style=\"display:inline-block;\"><img src=\"https://static-dev.rqmob.com/test/sa/20210804/42728fc75ca1bdadb5ab20fc3b84900b__FILE_CM____FILE_CM480_720____WEBP__.png\" width=\"320px\" height=\"50px\" /></a><script type=\"text/javascript\">window.MidasHTML = (function() {  this.$el = undefined;  this.args = {};  this.isViewable = false;  var bindClick = function() {    click_trackers = this.args.click_trackers;    target_url = this.args.target_url;    this.$el.onclick = function() {      emitTrackers(click_trackers);      window.open(target_url);    }  };  var emitTrackers = function emitTrackers(urls) {    urls.forEach(function(url) {      let obj = document.createElement(\"img\");              obj.src = url;              obj.style.display=\"none\";              this.$el.appendChild(obj);    });  };  var viewableCheck = function() {    if (this.isViewable) {  return;    }    var viewPortHeight = window.innerHeight || document.documentElement.clientHeight;    var viewPortWidth = window.innerWidth || document.documentElement.clientWidth;    var rec = this.$el.getBoundingClientRect();    this.isViewable = (rec.top >= -rec.height / 2 && rec.left >= -rec.width / 2 && rec.bottom <= viewPortHeight + rec.height / 2 && rec.right <= viewPortWidth + rec.width / 2);    if (this.isViewable) {      emitTrackers(args.impression_trackers);      bindClick();      this.isViewable = true;      clearInterval(this.timer)    }  };  var init = function(args) {    this.args = args;    this.$el = document.querySelector(\".\" + args.scope);    this.img = (this.$el.getElementsByTagName('img') || [])[0];    this.img.onload = () =>viewableCheck();    this.timer = setInterval(() =>viewableCheck(), 300);  };  return function(args) {    init(args);  }})();MidasHTML({\"click_trackers\":[\"https://midas-tracker-test.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa8c3eb6cb3763be39af447238100277632423c9c212f3987802acb093fa8f226d2beb00ad9aa5d901a36db98e81c1c0f1639ad363decc476977f6ba1dcb36318671a7a606d34961563c37535b94719f7eb4a8d53d8b3c80d002386ea6227bc2e50cdbcaa0c40a29bee9ef33b63c3f56ae4c59790d02b2be9ce6be9598e84f92c0efb7e9fdcf311fb0326d959dbd306031f78ae6a4a34675ad8bb6e84571c015638463b14fab8eded30cabefcf16c758eac517853709909da5be52230975657723bd0182b8eb7e92423a55066d07ab9c25a2c38cb0df2af9462c41155773054912137f7f508187acdfde64036bbcc7108237648df4168089d1ce5c8bae76768ae1f5a7cbda8f78a3c788123653da1a5f9294f7f410ac5a440063a7a62443efae33253b0e2bb16ed36a35b8720a1a75cd3a053a8f6415a00ecb94de70f89dff8f1e9dd5c1317a91c63f186f6e20d346da0aa4bbb9699eac716e961ac71a8048f0ad68c64b5e6ef9b3fec4e7969facea589f05d3fd1e9db885bcfea115dd393addc945f6de28f8ee1c2706e225370fc925762ef0ecb7317c28478b40b09f7b7611fc975cb19ea99226b086ca9c98895c8b86f12fa79b8086c1a3cff9f768f9b729c65121107709120f269c2ea863bda8797e77a98e3f177128fcbb4f46da9addbb1da7ef21f9aef6d0b9b1f4890d3cf764037f056e83dc7ed96a55cfab626fcf5903476d16ece901558cb0c2edc5a43cc44e9d2501eabccb23ead\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiYTEyNzFlY2EtZWZhMi00ZjlmLTg5MDQtYTg1M2FmZWMxMjg5Iiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwic2NyZWVuX3NpemUiOiIweDAiLCJuZXR3b3JrX3R5cGUiOjcsInBhY2thZ2VfbmFtZSI6InRydWVjYWxsZXIiLCJjb3VudHJ5IjoiaWQiLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyODYwLCJwb3NfaWQiOiIyMTUzIiwiYWRfaWQiOjEyODI2MywiYWRfcGFja2FnZV9uYW1lIjoiY29tLm1pZ28ubW9iaWxlIiwiY2lkIjo0NzUyMiwiY3RfY3ZyIjowLjAwMzkzNjAxNjc0OSwiYmlkX3ByaWNlIjoxNTAwMDAwMCwiZWNwbSI6NTkwNDAyNTEsImRzcF9uYW1lIjoiU2hhcmVpdCIsImF0dHJfcGxhdGZvcm0iOjEsImlzX2F1dG9fZG93bmxvYWQiOjEsImFkc2V0X2lkIjoyMzU1LCJhZF9uYW1lIjoi5bm_5ZGKMSIsImFkc2V0X25hbWUiOiJiYW5uZXIyNiIsInBoeV9wb3MiOiIyMTUzIn1dLCJtaWRhc192ZXJzaW9uIjoiMi4wIiwiYXBwX2lkIjoidHJ1ZWNhbGxlciJ9\&sid=__SID__\",\"http://ping-test.rqmob.com/click?ad=广告1\&ad_id=128263\&ad_type={ad_type}\&adpos_id=2153\&adset={adset}\&adset_id=2355\&advid=29\&amp_app_id=10053\&android_id=\&app_id=truecaller\&app_type=3\&beyla_id=\&c={c}\&c_id=47522\&campid=1440793\&channel_pkg=truecaller\&channel_pkg_ver=0\&cost_currency={cost_currency}\&cost_model={cost_model}\&cost_value={cost_value}\&country_code=id\&cut_type={cut_type}\&device_id=\&ext_info={ext_info}\&gaid=\&imei={imei}\&imsi={imsi}\&ip=1.1.1.1\&is_offline=1\&is_pre_install={is_pre_install}\&midas_camp_id=2860\&midas_traffic_type=1\&os_version=\&other_category={other_category}\&package_type={package_type}\&pkg=com.migo.mobile\&placement=2153\&platform=adshonor\&real_attrplat=1\&remote_ip=1.1.1.1\&requestid=a1271eca-efa2-4f9f-8904-a853afec1289\&sid={sid}\&site_id={site_id}\&uagent=\"],\"impression_trackers\":[\"https://midas-tracker-test.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa8c3eb6cb3763be39af447238100277632423c9c212f3987802acb093fa8f226d2beb00ad9aa5d901a36db98e81c1c0f1639ad363decc476977f6ba1dcb36318671a7a606d34961563c37535b94719f7eb4a8d53d8b3c80d002386ea6227bc2e50cdbcaa0c40a29bee9ef33b63c3f56ae4c59790d02b2be9ce6be9598e84f92c0efb7e9fdcf311fb0326d959dbd306031f78ae6a4a34675ad8bb6e84571c015638463b14fab8eded30cabefcf16c758eac517853709909da5be52230975657723bd0182b8eb7e92423a55066d07ab9c25a2c38cb0df2af9462c41155773054912137f7f508187acdfde64036bbcc7108237648df4168089d1ce5c8bae76768ae1f5a7cbda8f78a3c788123653da1a5f9294f7f410ac5a440063a7a62443efae33253b0e2bb16ed36a35b8720a1a75cd3a053a8f6415a00ecb94de70f89dff8f1e9dd5c1317a91c63f186f6e20d346da0aa4bbb9699eac716e961ac71a8048f0ad68c64b5e6ef9b3fec4e7969facea589f05d3fd1e9db885bcfea115dd393addc945f6de28f8ee1c2706e225370fc925762ef0ecb7317c28478b40b09f7b7611fc975cb19ea99226b086ca9c98895c8b86f12fa79b8086c1a3cff9f768f9b729c65121107709120f269c2ea863bda8797e77a98e3f177128fcbb4f46da9addbb1da7ef21f9aef6d0b9b1f4890d3cf764037f056e83dc7ed96a55cfab626fcf5903476d16ece901558cb0c2edc5a43cc43ecc8431995c0eaa2ffa3eba822597172e50f\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiJhMTI3MWVjYS1lZmEyLTRmOWYtODkwNC1hODUzYWZlYzEyODkiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsIm5ldHdvcmtfdHlwZSI6NywicGFja2FnZV9uYW1lIjoidHJ1ZWNhbGxlciIsImNvdW50cnkiOiJpZCIsIlBhcmFtcyI6W3siY2FtcGFpZ25faWQiOjI4NjAsInBvc19pZCI6IjIxNTMiLCJhZF9pZCI6MTI4MjYzLCJhZF9wYWNrYWdlX25hbWUiOiJjb20ubWlnby5tb2JpbGUiLCJjaWQiOjQ3NTIyLCJjdF9jdnIiOjAuMDAzOTM2MDE2NzQ5LCJiaWRfcHJpY2UiOjE1MDAwMDAwLCJlY3BtIjo1OTA0MDI1MSwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MSwiaXNfYXV0b19kb3dubG9hZCI6MSwiYWRzZXRfaWQiOjIzNTUsImFkX25hbWUiOiLlub_lkYoxIiwiYWRzZXRfbmFtZSI6ImJhbm5lcjI2IiwicGh5X3BvcyI6IjIxNTMifV0sIm1pZGFzX3ZlcnNpb24iOiIyLjAiLCJhcHBfaWQiOiJ0cnVlY2FsbGVyIn0\&sid=__SID__\"],\"scope\":\"_rnd_ad_128263\",\"target_url\":\"https://play.google.com/store/apps/details?id=com.migo.mobile\&hl=en\"});</script>",
                    "adid": "128263",
                    "bundle": "com.migo.mobile",
                    "crid": "47522",
                    "cid": "76d7c0780ceb8fbf964c102ebc16d75f",
                    "w": 320,
                    "h": 50,
                    "adomain": ["https://landingpage.example.com"]
                }
            ]
        }
    ],
    "cur": "USD"
}
```
