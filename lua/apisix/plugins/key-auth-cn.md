[中文](key-auth-cn.md) [英文](key-auth.md)

# Summary
- [**key-auth**](#key-auth)
- [**Quickstart**](#quickstart)
- [**Benchmark**](#benchmark)
- [**Development**](#development)


# key-auth

*NOTE* not finished yet.

Key-auth is an authentication plugin, it should work with `consumer` together.

Here is an example of binding to specified plugin, such as `key-auth`:

```shell
$ curl http://127.0.0.1:2379/v2/keys/plugins/key-auth/consumers\?recursive\=true | python -m json.tool
{
    "action": "get",
    "node": {
        "createdIndex": 1600,
        "dir": true,
        "key": "/plugins/key-auth/consumers",
        "modifiedIndex": 1600,
        "nodes": [
            {
                "createdIndex": 1603,
                "key": "/plugins/key-auth/consumers/ShunFeng",
                "modifiedIndex": 1603,
                "value": "{\"key\":\"kkkey\",\"id\":\"ShunFeng\"}"
            }
        ]
    }
}

$ curl http://127.0.0.1:2379/v2/keys/consumers\?recursive\=true | python -m json.tool
{
    "action": "get",
    "node": {
        "createdIndex": 1607,
        "dir": true,
        "key": "/consumers",
        "modifiedIndex": 1607,
        "nodes": [
            {
                "createdIndex": 1608,
                "key": "/consumers/ShunFeng",
                "modifiedIndex": 1608,
                "value": "{\"plugins\":{\"key-auth\":{\"key\":\"dddxxyyy\"}}}"
            }
        ]
    }
}
```

## Attributes

* `key`: 不同的 `consumer` 对象应该使用不同的值，它应该是唯一的。
