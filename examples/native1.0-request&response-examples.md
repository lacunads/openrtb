## Native Icon(1:1) Request Example
```json
{
    "id": "123",
    "imp": [{
        "id": "1",
        "tagid": "2049-abc-efg",
        "bidfloor": 0.01,
        "bidfloorcur": "USD",
        "native": {
            "request": "{\"native\":{\"assets\":[{\"required\":1,\"img\":{\"type\":1,\"wmin\":84,\"hmin\":84}}]}}",
            "ver": "1.0"
        },
        "instl": 0
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

## Native Icon(1:1) Response Example
```json
{
    "id": "123",
    "bidid": "47b61fdb-0c63-46fc-9343-df78cd5b700f",
    "seatbid": [{
        "bid": [{
            "id": "47b61fdb-0c63-46fc-9343-df78cd5b700f",
            "impid": "1",
            "price": 289,
            "nurl": "http://midas-tracker-dev.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b670a47da2e4cfc471bc12cab9b8b93ea9f6096bc3754a4504199138bfc3de2175b25964e6353ca9390f6b7d21d46562d114b3ce6b79aff194ecdf27e608df0042697e7b0649503d67118df10c3755021e9f0de8f7a9b81239631fcaec5085653cc924139de74a362dd9e496589f008a5fe08421489a154726e484f2a9ffd7974a17970b211becc8a6e0cbeb0da71a2ae9adeb03e38ccd710ae582d51af0d38435548613dd6ccc224e2043f773fb9d19f781248676bd6cfeb60aebed339572462c42954267f6d5674eb418481a076e1e93a80211802c27dbe661bc5261764e6ce987657027a6622954100b11934fd1e5b5034a26c4eef9d554705b9f2ac51c3f0bd4a70dec9eb1e3de6f8fefd4f565a4c11a76f3c0cdf2b039cde4bc985eb65e5f5d73ef36b82b0a67ac3031310b383067f90eb6a5ae7259c9888337e30b69a5c1f0c089e4014766a861d9e6f391a6659687391ba1c3f8b3e4c1335b8a729d305b73b985ebd4e063cf47ca2b38f3312ab92df818eaf56342bea6633b7e9d2ae195fbf5200646ea3b3afaf413a76f1c6785087c65feec214112cbc835df6f6fcab32fdc31d1288e01128279a527a8c9601e290cbf7a138230eee2eaf3023cb15&auction_price=${AUCTION_PRICE}&sid=__SID__",
            "adm":"{\"native\":{\"ver\":\"1.0\",\"assets\":[{\"img\":{\"type\":1,\"url\":\"http://static-dev.rqmob.com/test/sa/20210710/53da2d2e6b4f1482ecc5afd2c15bc824__FILE_CM____FILE_CM480_720____WEBP__.png\",\"w\":84,\"h\":84}}],\"link\":{\"url\":\"https://play.google.com/store/apps/details?id=com.janel.doctor.ear\&hl=en\",\"clicktrackers\":[\"http://midas-tracker-dev.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b670a47da2e4cfc471bc12cab9b8b93ea9f6096bc3754a4504199138bfc3de2175b25964e6353ca9390f6b7d21d46562d114b3ce6b79aff194ecdf27e608df0042697e7b0649503d67118df10c3755021e9f0de8f7a9b81239631fcaec5085653cc924139de74a362dd9e496589f008a5fe08421489a154726e484f2a9ffd7974a17970b211becc8a6e0cbeb0da71a2ae9adeb03e38ccd710ae582d51af0d38435548613dd6ccc224e2043f773fb9d19f781248676bd6cfeb60aebed339572462c42954267f6d5674eb418481a076e1e93a80211802c27dbe661bc5261764e6ce987657027a6622954100b11934fd1e5b5034a26c4eef9d554705b9f2ac51c3f0bd4a70dec9eb1e3de6f8fefd4f565a4c11a76f3c0cdf2b039cde4bc985eb65e5f5d73ef36b82b0a67ac3031310b383067f90eb6a5ae7259c9888337e30b69a5c1f0c089e4014766a861d9e6f391a6659687391ba1c3f8b3e4c1335b8a729d305b73b985ebd4e063cf47ca2b38f3312ab92df818eaf56342bea6633b7e9d2ae195fbf5200646ea3b3afaf413a76f1c6785087c65feec214112cbc835df6f6fcab32fdc31d1288e01128279a527a8c9601f19dd0f5a75a3f7f38f1\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiNDdiNjFmZGItMGM2My00NmZjLTkzNDMtZGY3OGNkNWI3MDBmIiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwic2NyZWVuX3NpemUiOiIweDAiLCJjb3VudHJ5IjoiaWQiLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyMjM4LCJwb3NfaWQiOiIyMDQ5IiwiYWRfaWQiOjEwMDc2NiwiY2FtcF9uYW1lIjoicGFubHVoLXNhbiIsImFkX3BhY2thZ2VfbmFtZSI6ImNvbS5qYW5lbC5kb2N0b3IuZWFyIiwiY2lkIjozODgwMywiYmlkX3ByaWNlIjoxMjMwMDAwMDAsImVjcG0iOjI4OTU1MzgwNCwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MiwiYWRzZXRfaWQiOjEzNTAsImFkX25hbWUiOiJTQU4tU0RLIiwiYWRzZXRfbmFtZSI6IlNBTi1TREsiLCJwaHlfcG9zIjoiMjA0OSJ9XSwibWlkYXNfdmVyc2lvbiI6IjIuMCJ9\&sid=__SID__\"]},\"imptrackers\":[\"http://midas-tracker-dev.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b670a47da2e4cfc471bc12cab9b8b93ea9f6096bc3754a4504199138bfc3de2175b25964e6353ca9390f6b7d21d46562d114b3ce6b79aff194ecdf27e608df0042697e7b0649503d67118df10c3755021e9f0de8f7a9b81239631fcaec5085653cc924139de74a362dd9e496589f008a5fe08421489a154726e484f2a9ffd7974a17970b211becc8a6e0cbeb0da71a2ae9adeb03e38ccd710ae582d51af0d38435548613dd6ccc224e2043f773fb9d19f781248676bd6cfeb60aebed339572462c42954267f6d5674eb418481a076e1e93a80211802c27dbe661bc5261764e6ce987657027a6622954100b11934fd1e5b5034a26c4eef9d554705b9f2ac51c3f0bd4a70dec9eb1e3de6f8fefd4f565a4c11a76f3c0cdf2b039cde4bc985eb65e5f5d73ef36b82b0a67ac3031310b383067f90eb6a5ae7259c9888337e30b69a5c1f0c089e4014766a861d9e6f391a6659687391ba1c3f8b3e4c1335b8a729d305b73b985ebd4e063cf47ca2b38f3312ab92df818eaf56342bea6633b7e9d2ae195fbf5200646ea3b3afaf413a76f1c6785087c65feec214112cbc835df6f6fcab32fdc31d1288e01128279a527a8c9601f698cae6a06433d213ad0e27e61ecbf359716f\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiI0N2I2MWZkYi0wYzYzLTQ2ZmMtOTM0My1kZjc4Y2Q1YjcwMGYiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsImNvdW50cnkiOiJpZCIsIlBhcmFtcyI6W3siY2FtcGFpZ25faWQiOjIyMzgsInBvc19pZCI6IjIwNDkiLCJhZF9pZCI6MTAwNzY2LCJjYW1wX25hbWUiOiJwYW5sdWgtc2FuIiwiYWRfcGFja2FnZV9uYW1lIjoiY29tLmphbmVsLmRvY3Rvci5lYXIiLCJjaWQiOjM4ODAzLCJiaWRfcHJpY2UiOjEyMzAwMDAwMCwiZWNwbSI6Mjg5NTUzODA0LCJkc3BfbmFtZSI6IlNoYXJlaXQiLCJhdHRyX3BsYXRmb3JtIjoyLCJhZHNldF9pZCI6MTM1MCwiYWRfbmFtZSI6IlNBTi1TREsiLCJhZHNldF9uYW1lIjoiU0FOLVNESyIsInBoeV9wb3MiOiIyMDQ5In1dLCJtaWRhc192ZXJzaW9uIjoiMi4wIn0\&sid=__SID__\"]}}",
            "adid": "100766",
            "crid": "102982",
            "cid": "76d7c0780ceb8fbf964c102ebc16d75f",
            "adomain": ["https://landingpage.example.com"]
        }]
    }],
    "cur": "USD"
}
```





## Native Banner (1.91:1) Request Example

```json
{
    "id": "123",
    "imp": [{
        "id": "1",
        "tagid": "2049-abcd-efg",
        "bidfloor": 0.01,
        "bidfloorcur": "USD",
        "native": {
            "request": "{\"native\":{\"assets\":[{\"required\":1,\"img\":{\"type\":3,\"wmin\":600,\"hmin\":314}}]}}",
            "ver": "1.0"
        },
        "instl": 0
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

## Native Banner(1.91:1) Response Example
```json
{
    "id": "123",
    "bidid": "176ffe99-ee8a-4558-b023-2ba7df62b529",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "176ffe99-ee8a-4558-b023-2ba7df62b529",
                    "impid": "1",
                    "price": 0.002,
                    "nurl": "https://midas-tracker-test.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d042bb2c31780f1edaba4a636848300c31077f7c1c46622909fda3c19eac1dd61aa76edc8998231bb839bb8276a5e100141079f3852637d89551b2b28591979fcf75e874197003ac91dde8a992057cae1fd08e96662b9b35b03b3fcba86edc3bb884b268acaa37e8c04f115d0a57cb9f360fb72ef052fc48a3159d27b4d419e6ffeb7fe7bc66acf6a3280b315c7fd9bcb1c1b2a9e61c14dfb37b8f92ab5804197c86b2012cdf877f74f7247bf17b4b7578c1dca7a8ff0a83c1711fbcb8580064c31be9cc903e3d64c302ddcdfaed3c46c69a343d17ebae74183a5a18fdd29521596290fd6bd9443ac9956587ef86d86b0a3a6c0182d7f39ef670f9e8dd18e6fedc2cff5b2b38ca24e0b9ee5e8dd28db659785f4986253b26801e7b6b7870f26a6de4b6eaa543070f4f63f88e58c89f70ea9421e8282993c4d2823b85e517ad340d36b626ba4ecd9d7b7cc28308056f9accb3ac0bf31e0c9f67dd19509e6b74e5cb0ec83a459f0c7e7794e1beebbbac12a4f7ec60e4308df4df9b2b71f2a667e094a373063583640651441258fcaae5f24ceab8bfb430e03af313d00a9f56eab81e24419a6983903e86b9a203cff6db4d926c1b6e13436a714ed25fa534edbe53047b0b697964e73122073db1a3ce6a43ca15bc92200b6956348a63dddbd1a3a31c620b9dddb762e65167208710532a65182b25f53d16acddbb66cc7143ca4df560f242503ee53ced324d5f063b60d12df7a6&auction_price=${AUCTION_PRICE}&sid=__SID__",
                    "adm":"{\"native\":{\"ver\":\"1.0\",\"assets\":[{\"img\":{\"type\":3,\"url\":\"https://static-dev.rqmob.com/test/sa/20200812/871d8298ad57f3ef9d23dc608947a3bd__FILE_CM____FILE_CM480_720__.jpg\",\"w\":600,\"h\":314}}],\"link\":{\"url\":\"https://play.google.com/store/apps/details?id=com.tokopedia.tkpd\&hl=en\",\"clicktrackers\":[\"https://midas-tracker-test.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d042bb2c31780f1edaba4a636848300c31077f7c1c46622909fda3c19eac1dd61aa76edc8998231bb839bb8276a5e100141079f3852637d89551b2b28591979fcf75e874197003ac91dde8a992057cae1fd08e96662b9b35b03b3fcba86edc3bb884b268acaa37e8c04f115d0a57cb9f360fb72ef052fc48a3159d27b4d419e6ffeb7fe7bc66acf6a3280b315c7fd9bcb1c1b2a9e61c14dfb37b8f92ab5804197c86b2012cdf877f74f7247bf17b4b7578c1dca7a8ff0a83c1711fbcb8580064c31be9cc903e3d64c302ddcdfaed3c46c69a343d17ebae74183a5a18fdd29521596290fd6bd9443ac9956587ef86d86b0a3a6c0182d7f39ef670f9e8dd18e6fedc2cff5b2b38ca24e0b9ee5e8dd28db659785f4986253b26801e7b6b7870f26a6de4b6eaa543070f4f63f88e58c89f70ea9421e8282993c4d2823b85e517ad340d36b626ba4ecd9d7b7cc28308056f9accb3ac0bf31e0c9f67dd19509e6b74e5cb0ec83a459f0c7e7794e1beebbbac12a4f7ec60e4308df4df9b2b71f2a667e094a373063583640651441258fcaae5f24ceab8bfb430e03af313d00a9f56eab81e24419a6983903e86b9a203cff6db4d926c1b6e13436a714ed25fa534edbe53047b0b697964e73122073db1a3ce6a43ca15bc92200b6956348a63dddbd1a3a31c620b9dddb762e65167208710532a65182b25f53d16acddbb66cc7143ca4df560f2424333fe3eeb5051406144\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiMTc2ZmZlOTktZWU4YS00NTU4LWIwMjMtMmJhN2RmNjJiNTI5Iiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwic2NyZWVuX3NpemUiOiIweDAiLCJwYWNrYWdlX25hbWUiOiLlsI_nsbPnsbMiLCJjb3VudHJ5IjoiaWQiLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyODEzLCJwb3NfaWQiOiIyMDQ5IiwiYWRfaWQiOjEyNzY3NCwiYWRfcGFja2FnZV9uYW1lIjoiY29tLnRva29wZWRpYS50a3BkIiwiY2lkIjozNjQ0OSwiY3RfY3ZyIjowLjAxMTM3MTU2NzU0LCJiaWRfcHJpY2UiOjEwMDAwMDAwLCJlY3BtIjoxMTM3MTU2NzUsImRzcF9uYW1lIjoiU2hhcmVpdCIsImF0dHJfcGxhdGZvcm0iOjIsImlzX2F1dG9fZG93bmxvYWQiOjEsImFkc2V0X2lkIjoyMzAyLCJhZF9uYW1lIjoi5bm_5ZGKLW5hdGl2ZS3op4TmoLwxIiwiYWRzZXRfbmFtZSI6InJ0Yi1iYW5uZXIteXN5LWZpbmFsIiwicGh5X3BvcyI6IjIwNDkifV0sIm1pZGFzX3ZlcnNpb24iOiIyLjAiLCJhcHBfaWQiOiLlsI_nsbPnsbMifQ\&sid=__SID__\",\"http://ping-test.rqmob.com/click?ad=广告-native-规格1\&ad_id=127674\&ad_type={ad_type}\&adpos_id=2049\&adset={adset}\&adset_id=2302\&advid=29\&amp_app_id=8057\&android_id=\&app_id=小米米\&app_type=3\&beyla_id=\&c={c}\&c_id=36449\&campid=1420697\&channel_pkg=小米米\&channel_pkg_ver=0\&cost_currency={cost_currency}\&cost_model={cost_model}\&cost_value={cost_value}\&country_code=id\&cut_type={cut_type}\&device_id=\&ext_info={ext_info}\&gaid=\&imei={imei}\&imsi={imsi}\&ip=1.1.1.1\&is_offline=1\&is_pre_install={is_pre_install}\&midas_camp_id=2813\&midas_traffic_type=1\&os_version=\&other_category={other_category}\&package_type={package_type}\&pkg=com.tokopedia.tkpd\&placement=2049\&platform=adshonor\&real_attrplat=2\&remote_ip=1.1.1.1\&requestid=176ffe99-ee8a-4558-b023-2ba7df62b529\&sid={sid}\&site_id={site_id}\&uagent=\"]},\"imptrackers\":[\"https://midas-tracker-test.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d042bb2c31780f1edaba4a636848300c31077f7c1c46622909fda3c19eac1dd61aa76edc8998231bb839bb8276a5e100141079f3852637d89551b2b28591979fcf75e874197003ac91dde8a992057cae1fd08e96662b9b35b03b3fcba86edc3bb884b268acaa37e8c04f115d0a57cb9f360fb72ef052fc48a3159d27b4d419e6ffeb7fe7bc66acf6a3280b315c7fd9bcb1c1b2a9e61c14dfb37b8f92ab5804197c86b2012cdf877f74f7247bf17b4b7578c1dca7a8ff0a83c1711fbcb8580064c31be9cc903e3d64c302ddcdfaed3c46c69a343d17ebae74183a5a18fdd29521596290fd6bd9443ac9956587ef86d86b0a3a6c0182d7f39ef670f9e8dd18e6fedc2cff5b2b38ca24e0b9ee5e8dd28db659785f4986253b26801e7b6b7870f26a6de4b6eaa543070f4f63f88e58c89f70ea9421e8282993c4d2823b85e517ad340d36b626ba4ecd9d7b7cc28308056f9accb3ac0bf31e0c9f67dd19509e6b74e5cb0ec83a459f0c7e7794e1beebbbac12a4f7ec60e4308df4df9b2b71f2a667e094a373063583640651441258fcaae5f24ceab8bfb430e03af313d00a9f56eab81e24419a6983903e86b9a203cff6db4d926c1b6e13436a714ed25fa534edbe53047b0b697964e73122073db1a3ce6a43ca15bc92200b6956348a63dddbd1a3a31c620b9dddb762e65167208710532a65182b25f53d16acddbb66cc7143ca4df560f2424436e42dec6e5d6df97031d9516c8218aa33ab\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiIxNzZmZmU5OS1lZThhLTQ1NTgtYjAyMy0yYmE3ZGY2MmI1MjkiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsInBhY2thZ2VfbmFtZSI6IuWwj-exs-exsyIsImNvdW50cnkiOiJpZCIsIlBhcmFtcyI6W3siY2FtcGFpZ25faWQiOjI4MTMsInBvc19pZCI6IjIwNDkiLCJhZF9pZCI6MTI3Njc0LCJhZF9wYWNrYWdlX25hbWUiOiJjb20udG9rb3BlZGlhLnRrcGQiLCJjaWQiOjM2NDQ5LCJjdF9jdnIiOjAuMDExMzcxNTY3NTQsImJpZF9wcmljZSI6MTAwMDAwMDAsImVjcG0iOjExMzcxNTY3NSwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MiwiaXNfYXV0b19kb3dubG9hZCI6MSwiYWRzZXRfaWQiOjIzMDIsImFkX25hbWUiOiLlub_lkYotbmF0aXZlLeinhOagvDEiLCJhZHNldF9uYW1lIjoicnRiLWJhbm5lci15c3ktZmluYWwiLCJwaHlfcG9zIjoiMjA0OSJ9XSwibWlkYXNfdmVyc2lvbiI6IjIuMCIsImFwcF9pZCI6IuWwj-exs-exsyJ9\&sid=__SID__\"]}}",
                    "adid": "127674",
                    "bundle": "com.tokopedia.tkpd",
                    "crid": 102982
                }
            ]
        }
    ],
    "cur": "USD"
}
```
