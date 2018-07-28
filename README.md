行情数据
行情数据主要是显示各个交易平台中数字货币的实时价格。为了给各个项目提供更全面的数据支持，现支持币种（项目）的详情。具体字段见图3   数据 
2．接口概述
2.1．根据平台名查询币币交易列表
（1）请求路径URL ：
http://www.hskjs.com/restful/{version}/getMarketByPName/{platformName}/{queryType}
请求数据说明：
version:版本号，目前是v1版本
platformName:平台名称，如huobi
queryType:排序条件
即（
1.按成交量倒序
2.按成交量升序
3.按成交额倒序
4.按成交额升序
5.按涨跌幅倒序
6.按涨跌幅升序
7.按最新价倒序
8.按最新价升序）
举例：
http://www.hskjs.com/restful/v1/getMarketByPName/huobi/1
（2）正确返回数据：
窗体顶端
{
    "state": true, 
    "obj": [
        {
            "_id": {
                "timestamp": 1532343520, 
                "machineIdentifier": 16481631, 
                "processIdentifier": 10156, 
                "counter": 7090246, 
                "time": 1532343520000, 
                "date": 1532343520000, 
                "timeSecond": 1532343520
            }, 
            "tsName": "trx", 
            "platformName": "huobi", 
            "dealPair": "usdt,btc,eth,ht", 
            "amount": 612665853.1353516, 
            "count": 27081, 
            "low": 0.032827, 
            "high": 0.039188, 
            "vol": 21772762.40894933, 
            "upRange": 0.08487010558416528, 
            "riseFall": -0.0029500000000000012, 
            "usdPrice": 0.037709
        }, 
        {
            "_id": {
                "timestamp": 1532343459, 
                "machineIdentifier": 16481631, 
                "processIdentifier": 10156, 
                "counter": 7090226, 
                "time": 1532343459000, 
                "date": 1532343459000, 
                "timeSecond": 1532343459
            }, 
            "tsName": "iost", 
            "platformName": "huobi", 
            "dealPair": "usdt,btc,eth,ht", 
            "amount": 364634657.1251097, 
            "count": 31482, 
            "low": 0.02192, 
            "high": 0.0244, 
            "vol": 8490816.352564221, 
            "upRange": 0.006554776219104768, 
            "riseFall": -0.00015699999999999742, 
            "usdPrice": 0.024109
        }
    ], 
    "msg": "请求成功", 
    "code": "0000"}
窗体底端

（3）返回数据说明：表 1 
id          	主键
tsName	项目英文简称
platformName	平台名称
dealPair	交易对
amount      	成交量
count       	成交笔数 
low         	最低价
high 	最高价
vol 	成交额, 即 sum(每一笔成交价 * 该笔的成交量)
upRange	涨幅
riseFall	涨跌
usdPrice	美元价格
表 1

返回数据说明补充：表 2
id          	主键
state	true:正确，false,qa错误
obj	返回数据
msg	返回状态说明
code     	状态码
表 2

返回状态码code说明：表 3
状态码        	说明
0000	请求成功
0001	请求失败
0002	暂无数据
0003	系统异常
0004	非法访问
0005	参数为空
0006	参数格式错误
0007	参数错误
0008	版本错误
表 3

2.2．根据币种名称查各平台此币种行情
（1）请求URL：
http://www.hskjs.com/{version}/getMarketByCoin/{coinName}/{queryType}

请求数据说明：
version:版本号，目前是v1版本
coinName:平台名称，如btc
queryType:排序条件
即（
1.按成交量倒序
2.按成交量升序
3.按成交额倒序
4.按成交额升序
5.按涨跌幅倒序
6.按涨跌幅升序
7.按最新价倒序
8.按最新价升序）
举例：
http://47.52.210.186:9081/restful/v1/getMarketByCoin/btc/1
（2）正确返回数据：
窗体顶端
{
    "state": true, 
    "obj": [
        {
            "_id": {
                "timestamp": 1532343439, 
                "machineIdentifier": 16481631, 
                "processIdentifier": 10156, 
                "counter": 7090206, 
                "time": 1532343439000, 
                "date": 1532343439000, 
                "timeSecond": 1532343439
            }, 
            "tsName": "btc", 
            "platformName": "huobi", 
            "dealPair": "usdt,btc,eth,ht", 
            "amount": 29404.54397436393, 
            "count": 302225, 
            "low": 7991.92, 
            "high": 8487.3, 
            "vol": 243275342.12857446, 
            "upRange": 0.027172053030094734, 
            "riseFall": -217.53999999999905, 
            "usdPrice": 8223.56
        }, 
        {
            "_id": {
                "timestamp": 1532343991, 
                "machineIdentifier": 3055513, 
                "processIdentifier": 30299, 
                "counter": 5463095, 
                "time": 1532343991000, 
                "date": 1532343991000, 
                "timeSecond": 1532343991
            }, 
            "tsName": "btc", 
            "platformName": "allcoin", 
            "dealPair": "usd,btc,eth,qtum,cnet", 
            "amount": 2371.0831, 
            "count": 0, 
            "low": 8092.4829, 
            "high": 8811.7588, 
            "vol": 0, 
            "upRange": 0.0336, 
            "riseFall": 0, 
            "usdPrice": 8378.275
        }
    ], 
    "msg": "请求成功", 
"code": "0000"}
（3）返回数据说明：
请参考表1，表2，表3
2.3．查询单个币种行情
（1）请求URL：
http://www.hskjs.com/{version}/getMarket/{platformName}/{coinName}
请求数据说明：
version:版本号，目前是v1版本
platformName:平台名称，如huobi
coinName:币名
举例：
http://www.hskjs.com/restful/v1/getMarket/huobi/btc
（2）正确返回数据：
窗体顶端
{
    "state": true, 
    "obj": {
        "_id": {
            "timestamp": 1532343439, 
            "machineIdentifier": 16481631, 
            "processIdentifier": 10156, 
            "counter": 7090206, 
            "time": 1532343439000, 
            "date": 1532343439000, 
            "timeSecond": 1532343439
        }, 
        "tsName": "btc", 
        "platformName": "huobi", 
        "dealPair": "usdt,btc,eth,ht", 
        "amount": 29445.885899217715, 
        "count": 302630, 
        "low": 7991.92, 
        "high": 8487.3, 
        "vol": 243624839.85607597, 
        "upRange": 0.03000708139095547, 
        "riseFall": -239.84000000000105, 
        "usdPrice": 8232.62
    }, 
    "msg": "请求成功", 
    "code": "0000"}
（3）返回数据说明：
请参考表1，表2，表3
