[中文](key-auth-cn.md) [英文](key-auth.md)

# Summary
- [**Name**](#name)
- [**Attributes**](#attributes)
- [**How To Enable**](#how-to-enable)
- [**Test Plugin**](#test-plugin)
- [**Disable Plugin**](#disable-plugin)


## Name

`key-auth` is an authentication plugin, it should work with `consumer` together.

Add Key Authentication (also sometimes referred to as an API key) to a Service or a Route. Consumers then add their key either in a querystring parameter or a header to authenticate their requests.

## Attributes

* `key`: different consumer objects should use different values, it should be unique.

## How To Enable

1. 创建一个 consumer 对象，并设置插件 `key-auth` 的值。

```shell
curl http://127.0.0.1:2379/v2/keys/consumers/ShunFeng -X PUT -d value='
{
    "id": "ShunFeng",
    "plugins": {
        "key-auth": {
            "key": "dddxxyyy"
        }
    }
}'
```

2. 创建 route 或 service 对象，开启 `key-auth` 插件。

```shell
curl http://127.0.0.1:2379/v2/keys/apisix/routes/1 -X PUT -d value='
{
	"methods": ["GET"],
	"uri": "/index.html",
	"id": 1,
	"plugin_config": {
		"key-auth": {}
	},
	"upstream": {
		"type": "roundrobin",
		"nodes": {
			"39.97.63.215:80": 1
		}
	}
}'
```

## Test Plugin



## Disable Plugin
