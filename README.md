# getObject
## 0. 前言
* 版本：第一版‧2018/2/13
* 作者：mi70
* 可以截取Object裡面的keys或values

## 1. 使用方式

#### 1.0 
引入以下這段js
```
var getObject = (function() {
        //抓長度
        var getLength = function(_obj) {
            return Object.keys(_obj).length;
        }
        //抓Object key
        var getKeys = function(_obj) {
            var _array = []; //put keys
            var _length = this.getLength(_obj); //get length
            //creat key group
            for (var i = 0; i < _length; i += 1) {
                _array.push(Object.keys(_obj)[i]); //push key to array
            }
            return _array;
        }
        //抓Object values
        var getValue = function(_obj) {
            var _array = []; //put keys
            var _length = this.getLength(_obj); //get length
            var _boolean = typeof Object.values === "function" ? true : false; //support or not
            //is support object.values
            if (_boolean) {
                for (var i = 0; i < _length; i += 1) {
                    _array.push(Object.values(_obj)[i]); //push key to array
                }
            } else {
                Object.keys(_obj).map(function(e) { _array.push(_obj[e]) }); //push key to array
            }
            return _array;
        }
        return {
            getLength: getLength,
            getKeys: getKeys,
            getVals: getValue
        }
    })()
```

#### 1.1
直接呼叫
>例如
```
var o = {
        item: {
            'first': { id: 1, name: 'winner' },
            'secound': { id: 2, name: 'spring' },
            'third': { id: 3, name: 'summer' },
        }
    };
 
      alert(getObject.getKeys(o.item))	//get key
      alert(getObject.getVals(o.item))	//get value
```


##### 其餘部分可以參考範例檔案 index.html
