## Interstial native(2:3) request exmpale
```json
{
    "id": "32f94228-52d3-4bce-be88-5dd1d799ae4f",
    "imp": [{
        "id": "1",
        "tagid": "100040-1002421",
        "bidfloor": 0.00001,
        "bidfloorcur": "USD",
        "secure": 0,
        "native": {
            "request": "{\"assets\":[{\"required\":1,\"img\":{\"type\":3,\"wmin\":640,\"hmin\":960}}], \"ver\":\"1.2\"}"
     },
     "instl": 1
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
    "tmax": 2000,
    "debug": 0
}

```

## Interstial native(2:3) Response Example
```json
{
    "id": "32f94228-52d3-4bce-be88-5dd1d799ae4f",
    "bidid": "efb9f60b-1dbd-4a29-9379-a110f37d4c05",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "efb9f60b-1dbd-4a29-9379-a110f37d4c05",
                    "impid": "1",
                    "price": 101,
                    "nurl": "https://midas-tracker-test.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa9c2e96cb376835e096062d72ffb45ecfa40d44d30180a9a413b654c20986fac3ea8f86e1493a6b8c3f6d4eba9365584d93a04dc4ddfda17a5d6b19e9aacfda060e0a278dcbf9894e7bd767ce36a2b23b20f6c0149fabf73ee15e0de80177c865da22a3d216142b0813066b842634f095b7a99a69ff70eb4e20f9f0809d719ddab69c9fde4608f051c3585f6bd0bd3d866c233ee09a0cb3c77327acfeb1c77d1d65ef0012101b4dd0e7c57385f8c9a303030f79a46032a1293f26fd0ff271a605335729a3b196c64624ea2c1cfbac187253926086223b91d89715738e4e6179a49e28dd3289fcddf6a70a8addc0f0558725bcf727f93ba982be7dcbacbede95f2634cb8693f951dbdc878e36f61236126c1114fd50c48b955c91255bc3f3b1c1544b2e98146e52c5030daaa9f26392697ca8643f83e64894f1d6526addcc0c350d22d085896bd3fe3644856f48ff742b4516619fd594914ca519ac4699192e5f07cb861249d7dac27c5b716571e2390f9974aaa4786dd37a647dc01128526590a6cce5e9473c27946b14237582d630bee8679debdbb5bae053f230ded17caa130bb97e1b8f5b6eec55ffca05eec5adcf16ed4343d7cef7cc30928a3f93efba4c4cbee00f05f3b8acfa202d0a497ae122fd0d571195c4a54ab142ce37dd3cc4863fb1510a7b2297f52eb5a268ce9512559806c9351efccf0b44d8ca7443aff1aa3066f282a844c6f448caf1ac8cd3aa1fb685cacdc2c8845329b46a08dbff8f540648b52e5679875cb9285ff39ea1db71210db61e6ca9b6ee1752d1823dad41ed5fd8184bdf74ed7fa3c4f578aaa92fd56bad67dd473b7bf95c96701140956b17fb1ea0734b1d89b79f861893712c3e6e80cf5dedd73274&auction_price=${AUCTION_PRICE}&sid=__SID__",
                    "adm":"{\"assets\":[{\"img\":{\"type\":3,\"url\":\"https://static-dev.rqmob.com/test/sa/20211021/db7e94c83ece871e8f8aa6b28d2843c1__FILE_CM____FILE_CM480_720____WEBP__.jpg\",\"w\":640,\"h\":960}}],\"link\":{\"url\":\"https://play.google.com/store/apps/details?id=cc.forestapp\&hl=en\",\"clicktrackers\":[\"https://midas-tracker-test.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa9c2e96cb376835e096062d72ffb45ecfa40d44d30180a9a413b654c20986fac3ea8f86e1493a6b8c3f6d4eba9365584d93a04dc4ddfda17a5d6b19e9aacfda060e0a278dcbf9894e7bd767ce36a2b23b20f6c0149fabf73ee15e0de80177c865da22a3d216142b0813066b842634f095b7a99a69ff70eb4e20f9f0809d719ddab69c9fde4608f051c3585f6bd0bd3d866c233ee09a0cb3c77327acfeb1c77d1d65ef0012101b4dd0e7c57385f8c9a303030f79a46032a1293f26fd0ff271a605335729a3b196c64624ea2c1cfbac187253926086223b91d89715738e4e6179a49e28dd3289fcddf6a70a8addc0f0558725bcf727f93ba982be7dcbacbede95f2634cb8693f951dbdc878e36f61236126c1114fd50c48b955c91255bc3f3b1c1544b2e98146e52c5030daaa9f26392697ca8643f83e64894f1d6526addcc0c350d22d085896bd3fe3644856f48ff742b4516619fd594914ca519ac4699192e5f07cb861249d7dac27c5b716571e2390f9974aaa4786dd37a647dc01128526590a6cce5e9473c27946b14237582d630bee8679debdbb5bae053f230ded17caa130bb97e1b8f5b6eec55ffca05eec5adcf16ed4343d7cef7cc30928a3f93efba4c4cbee00f05f3b8acfa202d0a497ae122fd0d571195c4a54ab142ce37dd3cc4863fb1510a7b2297f52eb5a268ce9512559806c9351efccf0b44d8ca7443aff1aa3066f282a844c6f448caf1ac8cd3aa1fb685cacdc2c8845329b46a08dbff8f540648b52e5679875cb9285ff39ea1db71210db61e6ca9b6ee1752d1823dad41ed5fd8184bdf74ed7fa3c4f578aaa92fd56bad67dd473b7bf95c96701140956b17fb1ea0734b1d89b78c8b0391774e22719c9b\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiZWZiOWY2MGItMWRiZC00YTI5LTkzNzktYTExMGYzN2Q0YzA1Iiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwicGxhdGZvcm0iOjEsIm9zX3ZlcnNpb24iOiI1LjEuMSIsImltZWkiOiJlY2FlOTA0MmYzZTU0OWE0ZmQxYWYyN2ExZWQzOGI1ZjY4MmZhM2NhIiwiYnJhbmQiOiJXSUtPIiwibW9kZWwiOiJzYW1zdW5nLXNtLWc5MDBhIiwic2NyZWVuX3NpemUiOiIweDAiLCJsYW5ndWFnZSI6ImVuIiwiZ2FpZCI6IjU3MzFiNGM4LTdjYzEtNGEwOS1iYjc3LTI0ZjIzN2Q5M2E2NiIsIm5ldHdvcmtfdHlwZSI6NywicGFja2FnZV9uYW1lIjoi5bCP57Gz5rWL6K-VLeadqOWwkeeRnDEiLCJjb3VudHJ5IjoiY24iLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyNjYyLCJwb3NfaWQiOiIyMDQxIiwiYWRfaWQiOjE2MDA0NywiYWRfcGFja2FnZV9uYW1lIjoiY2MuZm9yZXN0YXBwIiwiY2lkIjo3Mzc2NywiYmlkX3ByaWNlIjoxMDEwMDAwMDAsImVjcG0iOjEwMTAwMDAwMCwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MSwiaXNfYXV0b19kb3dubG9hZCI6MSwiYWRzZXRfaWQiOjIwOTIsImFkX25hbWUiOiLpqozor4HntKDmnZDmoLzlvI_mmK8zOTo2NDAqOTYwLXRlc3QiLCJhZHNldF9uYW1lIjoicnRiLXRydWVjYWxsZXItMS0yNi0yNyIsInBoeV9wb3MiOiIyMDQxIiwidHJhZmZpY190eXBlIjoxfV0sIm1pZGFzX3ZlcnNpb24iOiIyLjAiLCJhcHBfaWQiOiLlsI_nsbPmtYvor5Ut5p2o5bCR55GcMSJ9\&sid=__SID__\"]},\"imptrackers\":[\"https://midas-tracker-test.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa9c2e96cb376835e096062d72ffb45ecfa40d44d30180a9a413b654c20986fac3ea8f86e1493a6b8c3f6d4eba9365584d93a04dc4ddfda17a5d6b19e9aacfda060e0a278dcbf9894e7bd767ce36a2b23b20f6c0149fabf73ee15e0de80177c865da22a3d216142b0813066b842634f095b7a99a69ff70eb4e20f9f0809d719ddab69c9fde4608f051c3585f6bd0bd3d866c233ee09a0cb3c77327acfeb1c77d1d65ef0012101b4dd0e7c57385f8c9a303030f79a46032a1293f26fd0ff271a605335729a3b196c64624ea2c1cfbac187253926086223b91d89715738e4e6179a49e28dd3289fcddf6a70a8addc0f0558725bcf727f93ba982be7dcbacbede95f2634cb8693f951dbdc878e36f61236126c1114fd50c48b955c91255bc3f3b1c1544b2e98146e52c5030daaa9f26392697ca8643f83e64894f1d6526addcc0c350d22d085896bd3fe3644856f48ff742b4516619fd594914ca519ac4699192e5f07cb861249d7dac27c5b716571e2390f9974aaa4786dd37a647dc01128526590a6cce5e9473c27946b14237582d630bee8679debdbb5bae053f230ded17caa130bb97e1b8f5b6eec55ffca05eec5adcf16ed4343d7cef7cc30928a3f93efba4c4cbee00f05f3b8acfa202d0a497ae122fd0d571195c4a54ab142ce37dd3cc4863fb1510a7b2297f52eb5a268ce9512559806c9351efccf0b44d8ca7443aff1aa3066f282a844c6f448caf1ac8cd3aa1fb685cacdc2c8845329b46a08dbff8f540648b52e5679875cb9285ff39ea1db71210db61e6ca9b6ee1752d1823dad41ed5fd8184bdf74ed7fa3c4f578aaa92fd56bad67dd473b7bf95c96701140956b17fb1ea0734b1d89b78b8e198270702e5c84df49add919fd897dcfcf\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiJlZmI5ZjYwYi0xZGJkLTRhMjktOTM3OS1hMTEwZjM3ZDRjMDUiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJwbGF0Zm9ybSI6MSwib3NfdmVyc2lvbiI6IjUuMS4xIiwiaW1laSI6ImVjYWU5MDQyZjNlNTQ5YTRmZDFhZjI3YTFlZDM4YjVmNjgyZmEzY2EiLCJicmFuZCI6IldJS08iLCJtb2RlbCI6InNhbXN1bmctc20tZzkwMGEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsImxhbmd1YWdlIjoiZW4iLCJnYWlkIjoiNTczMWI0YzgtN2NjMS00YTA5LWJiNzctMjRmMjM3ZDkzYTY2IiwibmV0d29ya190eXBlIjo3LCJwYWNrYWdlX25hbWUiOiLlsI_nsbPmtYvor5Ut5p2o5bCR55GcMSIsImNvdW50cnkiOiJjbiIsIlBhcmFtcyI6W3siY2FtcGFpZ25faWQiOjI2NjIsInBvc19pZCI6IjIwNDEiLCJhZF9pZCI6MTYwMDQ3LCJhZF9wYWNrYWdlX25hbWUiOiJjYy5mb3Jlc3RhcHAiLCJjaWQiOjczNzY3LCJiaWRfcHJpY2UiOjEwMTAwMDAwMCwiZWNwbSI6MTAxMDAwMDAwLCJkc3BfbmFtZSI6IlNoYXJlaXQiLCJhdHRyX3BsYXRmb3JtIjoxLCJpc19hdXRvX2Rvd25sb2FkIjoxLCJhZHNldF9pZCI6MjA5MiwiYWRfbmFtZSI6IumqjOivgee0oOadkOagvOW8j-aYrzM5OjY0MCo5NjAtdGVzdCIsImFkc2V0X25hbWUiOiJydGItdHJ1ZWNhbGxlci0xLTI2LTI3IiwicGh5X3BvcyI6IjIwNDEiLCJ0cmFmZmljX3R5cGUiOjF9XSwibWlkYXNfdmVyc2lvbiI6IjIuMCIsImFwcF9pZCI6IuWwj-exs-a1i-ivlS3mnajlsJHnkZwxIn0\&sid=__SID__\"]}",
                    "adid": "160047",
                    "bundle": "cc.forestapp",
                    "crid": "73767",
                    "cid": "76d7c0780ceb8fbf964c102ebc16d75f",
                    "adomain": ["https://landingpage.example.com"]
                }
            ]
        }
    ],
    "cur": "USD"
 }

```