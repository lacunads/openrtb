## video request示例
```json
{
	"id": "32f94228-52d3-4bce-be88-5dd1d799ae4f",
	"imp": [{
		"id": "1",
		"tagid": "100040-1002421",
		"bidfloor": 1.00,
		"bidfloorcur": "USD",
		"secure": 0,
      "video": {
        "w": 640,
        "h": 480,
        "pos": 1,
        "startdelay": 0,
        "minduration": 5,
        "maxduration": 30,
        "maxextended": 30,
        "minbitrate": 300,
        "maxbitrate": 1500,
        "api": [
          1,
          2
        ],
        "protocols": [
          2,
          3
        ],
        "mimes": [
          "video/x-flv",
          "video/mp4",
          "application/x-shockwave-flash",
          "application/javascript"
        ],
        "linearity": 1,
        "boxingallowed": 1,
        "playbackmethod": [
          1,
          3
        ],
        "delivery": [
          2
        ],
        "battr": [
          13,
          14
        ],
        "companionad": [
          {
            "id": "1234567893-1",
            "w": 300,
            "h": 250,
            "pos": 1,
            "battr": [
              13,
              14
            ],
            "expdir": [
              2,
              4
            ]
          },
          {
            "id": "1234567893-2",
            "w": 728,
            "h": 90,
            "pos": 1,
            "battr": [
              13,
              14
            ]
          }
        ],
        "companiontype": [
          1,
          2
        ]
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
		"ip": "1.1.1.1",
		"geo": {
			"country": "IND",
			"type": 2
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



## video response example
```json
{
    "id": "a24fe97c-a63e-416d-a357-8f2e3c679b29",
    "bidid": "a24fe97c-a63e-416d-a357-8f2e3c679b29",
    "cur": "USD",
    "seatbid": [
        {
            "seat": "2",
            "group": 0,
            "bid": [
                {
                    "id": "1",
                    "impid": "1",
                    "price": 0.255,
                    "w": 720,
                    "h": 1280,
                    "lurl": "https://rtbtrack-asia.rtblab.net/simpleloss?p=339&d=65&loss={AUCTION_LOSS}&l_b={AUCTION_ID}&l_a={AUCTION_AD_ID}&l_p={AUCTION_PRICE}&l_m={AUCTION_MBR}",
                    "nurl": "https://rtbtrack-asia.rtblab.net/win?p=339&d=65&t=55bW10qLPxlzQAXbMZUcWsf-OhubisbBjtjwjqdktKIJr2dmjrh-OmixU60az2HDosUCkB_GdRKL0zk60bPraXxkcuFOontU8dzS2Paqo_YKQa3DNJAh50yUvRWiacOSfOxGfUDUVhYtGQ2Ab7dIdxVZmCvBgmyZKNbyBjvQqdl0QsOEF0wals32i2chByx2fJicH9S5WC8D09hUuJLxkQ96S1pteutWmGp8Csv6C62OOzBToqZBk3nqBrJuIZTfbUoUrEYH7kQ8SeL6ltrcNHIUcp8sS6OdXHkirwusfPbJ1ExBXYw-D-RoojdsZcwIeNx7SKhPHeOqCr3FoS1ziFmtMvkvODPVJGTVxVmHSh6Yjy8b4fPZ8cmvgjRH4hsQ-d8Y3c3rtSIrYdgoptniln2pCXNfMxtrJnWtd1BIeI_IogEQVgztsHhn1O19KhKV7KxmEh0Nsf2H0kSTDI-yaYQtHGegEkJHITBnedGLwTsLaE3ri_pl296s4wZNNs7UKkOTtNOd1QiNoLs5foAl_bpXb3ESxOfsyWFlAN_dSinbpgVWyJmS_TektfONub_N",
                    "adm": "<?xml version=\"1.0\" encoding=\"UTF-8\"?><VAST version=\"2.0\"><Ad><InLine><AdSystem><![CDATA[TaurusX]]></AdSystem><AdTitle>com.zhiliaoapp.musically</AdTitle><Impression><![CDATA[http://34.126.85.24:4000/imp?p=webeye&d=minidsp&b=com.zhiliaoapp.musically]]></Impression><Impression><![CDATA[https://rtbtrack-asia.rtblab.net/imp?p=339&d=65&t=55bW10qLPxlzQAXbMZUcWsf-OhubisbBjtjwjqdktKIJr2dmjrh-OmixU60az2HDosUCkB_GdRKL0zk60bPraXxkcuFOontU8dzS2Paqo_YKQa3DNJAh50yUvRWiacOSfOxGfUDUVhYtGQ2Ab7dIdxVZmCvBgmyZKNbyBjvQqdl0QsOEF0wals32i2chByx2fJicH9S5WC8D09hUuJLxkQ96S1pteutWmGp8Csv6C62OOzBToqZBk3nqBrJuIZTfbUoUrEYH7kQ8SeL6ltrcNHIUcp8sS6OdXHkirwusfPbJ1ExBXYw-D-RoojdsZcwIeNx7SKhPHeOqCr3FoS1ziFmtMvkvODPVJGTVxVmHSh6Yjy8b4fPZ8cmvgjRH4hsQ-d8Y3c3rtSIrYdgoptniln2pCXNfMxtrJnWtd1BIeI_IogEQVgztsHhn1O19KhKV7KxmEh0Nsf2H0kSTDI-yaYQtHGegEkJHITBnedGLwTsLaE3ri_pl296s4wZNNs7UKkOTtNOd1QiNoLs5foAl_bpXb3ESxOfsyWFlAN_dSinbpgVWyJmS_TektfONub_N&ns=&bs=&ap={AUCTION_PRICE}]]></Impression><Impression><![CDATA[https://adrta.com/i?clid=we&paid=we&avid=65&plid=1337026&caid=345135&siteId=0&kv1=720x1280&kv3=b3f1d810-952d-4b06-beff-2bdf0672d5e3&kv4=114.122.73.251&publisherId=339&kv7=339&kv11=a24fe97c-a63e-416d-a357-8f2e3c679b29&kv12=Vungle_SSP&kv16=-6.921700&kv17=107.607100&kv18=mobi.mangatoon.novel&kv19=b3f1d810-952d-4b06-beff-2bdf0672d5e3&kv26=Android&kv28=Vivo&kv24=Mobile_InApp&kv15=&kv23=&kv62=0&kv63=&kv25=Vungle_SSP&kv27=Mozilla%2F5.0+%28Linux%3B+Android+9%3B+vivo+1904+Build%2FPPR1.180610.011%3B+wv%29+AppleWebKit%2F537.36+%28KHTML%2C+like+Gecko%29+Version%2F4.0+Chrome%2F103.0.5060.71+Mobile+Safari%2F537.36]]></Impression><Error><![CDATA[https://rtbtrack-asia.rtblab.net/vasterror?p=339&d=65&c=1337026&b=a24fe97c-a63e-416d-a357-8f2e3c679b29&error=[ERRORCODE]]]></Error><Creatives><Creative><Linear><Duration>00:00:13</Duration><TrackingEvents></TrackingEvents><VideoClicks><ClickThrough><![CDATA[https://play.google.com/store/apps/details?id=com.zhiliaoapp.musically]]></ClickThrough><ClickTracking><![CDATA[https://rtbtrack-asia.rtblab.net/clk?p=339&d=65&t=55bW10qLPxlzQAXbMZUcWsf-OhubisbBjtjwjqdktKIJr2dmjrh-OmixU60az2HDosUCkB_GdRKL0zk60bPraXxkcuFOontU8dzS2Paqo_YKQa3DNJAh50yUvRWiacOSfOxGfUDUVhYtGQ2Ab7dIdxVZmCvBgmyZKNbyBjvQqdl0QsOEF0wals32i2chByx2fJicH9S5WC8D09hUuJLxkQ96S1pteutWmGp8Csv6C62OOzBToqZBk3nqBrJuIZTfbUoUrEYH7kQ8SeL6ltrcNHIUcp8sS6OdXHkirwusfPbJ1ExBXYw-D-RoojdsZcwIeNx7SKhPHeOqCr3FoS1ziFmtMvkvODPVJGTVxVmHSh6Yjy8b4fPZ8cmvgjRH4hsQ-d8Y3c3rtSIrYdgoptniln2pCXNfMxtrJnWtd1BIeI_IogEQVgztsHhn1O19KhKV7KxmEh0Nsf2H0kSTDI-yaYQtHGegEkJHITBnedGLwTsLaE3ri_pl296s4wZNNs7UKkOTtNOd1QiNoLs5foAl_bpXb3ESxOfsyWFlAN_dSinbpgVWyJmS_TektfONub_N]]></ClickTracking></VideoClicks><MediaFiles><MediaFile height=\"1280\" width=\"720\" type=\"video/mp4\" delivery=\"progressive\"><![CDATA[https://storage.googleapis.com/taurusx/adx-minidsp/creatives/com.zhiliaoapp.musically_720x1280.mp4]]></MediaFile></MediaFiles></Linear></Creative><Creative><CompanionAds><Companion width=\"720\" height=\"1280\"><CompanionClickThrough><![CDATA[https://storage.googleapis.com/taurusx/adx-minidsp/creatives/com.zhiliaoapp.musically_endcard_720x1280.jpg]]></CompanionClickThrough><TrackingEvents></TrackingEvents><CompanionClickTracking><![CDATA[https://rtbtrack-asia.rtblab.net/clk?p=339&d=65&t=55bW10qLPxlzQAXbMZUcWsf-OhubisbBjtjwjqdktKIJr2dmjrh-OmixU60az2HDosUCkB_GdRKL0zk60bPraXxkcuFOontU8dzS2Paqo_YKQa3DNJAh50yUvRWiacOSfOxGfUDUVhYtGQ2Ab7dIdxVZmCvBgmyZKNbyBjvQqdl0QsOEF0wals32i2chByx2fJicH9S5WC8D09hUuJLxkQ96S1pteutWmGp8Csv6C62OOzBToqZBk3nqBrJuIZTfbUoUrEYH7kQ8SeL6ltrcNHIUcp8sS6OdXHkirwusfPbJ1ExBXYw-D-RoojdsZcwIeNx7SKhPHeOqCr3FoS1ziFmtMvkvODPVJGTVxVmHSh6Yjy8b4fPZ8cmvgjRH4hsQ-d8Y3c3rtSIrYdgoptniln2pCXNfMxtrJnWtd1BIeI_IogEQVgztsHhn1O19KhKV7KxmEh0Nsf2H0kSTDI-yaYQtHGegEkJHITBnedGLwTsLaE3ri_pl296s4wZNNs7UKkOTtNOd1QiNoLs5foAl_bpXb3ESxOfsyWFlAN_dSinbpgVWyJmS_TektfONub_N&ec=1]]></CompanionClickTracking></Companion></CompanionAds></Creative></Creatives></InLine></Ad></VAST>",
                    "bundle": "com.zhiliaoapp.musically",
                    "iurl": "https://static-conversant-assist.rtblab.cc/R4zEsf0zjcfD1eC.jpg",
                    "cid": "345135",
                    "adid": "345135_1337026",
                    "crid": "1337026",
                    "cat": [
                        "IAB18"
                    ],
                    "adomain": [
                        "musically.zhiliaoapp.com"
                    ],
                    "attr": [
                        4
                    ],
                    "ext": {
                        "crtype": "VAST 2.0"
                    }
                }
            ]
        }
    ],
    "ext": {
        "source": ""
    }
}
```
 

