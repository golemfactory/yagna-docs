# API Reference

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/yajsapi.md) / Exports

## yajsapi

### Table of contents

* [crypto](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/crypto.md)
* [executor](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/executor.md)
* [executor/ctx](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/executor_ctx.md)
* [executor/events](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/executor_events.md)
* [executor/smartq](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/executor_smartq.md)
* [executor/strategy](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/executor_strategy.md)
* [executor/task](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/executor_task.md)
* [index](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/index.md)
* [package](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/package.md)
* [package/sgx](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/package_sgx.md)
* [package/vm](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/package_vm.md)
* [props](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/props.md)
* [props/base](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/props_base.md)
* [props/builder](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/props_builder.md)
* [props/com](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/props_com.md)
* [props/inf](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/props_inf.md)
* [rest](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/rest.md)
* [rest/activity](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/rest_activity.md)
* [rest/configuration](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/rest_configuration.md)
* [rest/market](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/rest_market.md)
* [rest/payment](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/rest_payment.md)
* [rest/resource](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/rest_resource.md)
* [storage](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/storage.md)
* [storage/gftp](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/storage_gftp.md)
* [storage/webdav](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/storage_webdav.md)
* [utils](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils.md)
* [utils/applyMixins](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_applymixins.md)
* [utils/asyncExitStack](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_asyncexitstack.md)
* [utils/asyncWith](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_asyncwith.md)
* [utils/asyncWrapper](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_asyncwrapper.md)
* [utils/callable](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_callable.md)
* [utils/cancellationToken](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_cancellationtoken.md)
* [utils/eventLoop](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_eventloop.md)
* [utils/getAllProperties](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_getallproperties.md)
* [utils/log](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_log.md)
* [utils/queue](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_queue.md)
* [utils/range](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_range.md)
* [utils/sleep](https://github.com/golemfactory/yagna-docs/tree/6a1da6498d6b82b65beb3776c75bc6edb59eab57/yajsapi/modules/utils_sleep.md)

