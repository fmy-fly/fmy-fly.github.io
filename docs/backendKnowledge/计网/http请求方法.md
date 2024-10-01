# http请求方法


## 一、GET
- GET请求用于从服务器获取资源，通常用于获取数据；
- GET请求的参数会附加在URL的末尾，可以通过URL参数传递数据；
- GET请求是幂等的，即多次请求同一个URL得到的结果应该是一样的，不会对服务器端产生影响；
- GET请求的数据传输量是有限的，受URL长度限制，一般用于获取数据；
- 该请求就像数据库的select（查询数据）操作一样。

```java

/**
 * 查看购物车
 * @return
 */
@GetMapping("/list")
@ApiOperation("查看购物车")
public Result<List<ShoppingCart>> list() {
    List<ShoppingCart> list = shoppingCartService.showShoppingCart();
    return Result.success(list);
}
```

## 二、PUT
- PUT请求用于向服务器更新或创建资源，通常用于更新一条记录或创建新资源；
- PUT请求的数据会放在请求体中，类似于POST请求；
- PUT请求是幂等的，即多次请求同一个URL得到的结果应该是一样的，不会对服务器端产生影响；
- PUT请求通常用于更新已存在的资源，需要提供完整的资源信息；
- 该请求就像数据库的update（更新数据）操作一样。
```java   
/**
 * 修改分类
 * @param categoryDTO
 * @return
 */
@PutMapping
@ApiOperation("修改分类")
public Result<String> update(@RequestBody CategoryDTO categoryDTO){
    categoryService.update(categoryDTO);
    return Result.success();
}
```

## 三、POST
- POST请求用于向服务器提交数据，通常用于提交表单数据或上传文件；
- POST请求的数据会放在请求体中，不会暴露在URL中；
- POST请求不是幂等的，即多次请求同一个URL可能会对服务器端产生影响，比如重复提交表单数据；
- POST请求的数据传输量较大，没有URL长度限制，适用于提交大量数据；
该请求就像数据库的insert（插入数据）操作一样。
```java
/**
 * 添加购物车
 * @param shoppingCartDTO
 * @return
 */
@PostMapping("/add")
@ApiOperation("添加购物车")
public Result add(@RequestBody ShoppingCartDTO shoppingCartDTO) {
    log.info("添加购物车，商品信息为：{}", shoppingCartDTO);
    shoppingCartService.addShoppingCart(shoppingCartDTO);
    return Result.success();
}
```
## 四、DELETE
- DELETE请求用于删除指定的资源；
- DELETE请求通常用于删除服务器上的资源，比如删除一条记录；
- DELETE请求是幂等的，即多次请求同一个URL得到的结果应该是一样的，不会对服务器端产生影响；
- 该请求就像数据库的delete（删除数据）操作一样。
```java  
    /**
 * 清空购物车
 * @return
 */
@DeleteMapping("/clean")
@ApiOperation("清空购物车")
public Result clean() {
    shoppingCartService.cleanShoppingCart();
    return Result.success();
}
```

## 总结
- GET请求用于获取资源，参数在URL中，幂等。
- POST请求用于提交数据，参数在请求体中，不幂等。
- PUT请求用于更新或创建资源，参数在请求体中，幂等。
- DELETE请求用于删除资源，幂等。
