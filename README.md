# 省市县数据 for Element

> 源数据取自 [https://github.com/getActivity/ProvinceJson]()



## 一、文件说明

- `province-element.json` 格式化的数据 <kbd>381kb</kbd>
- `province-element-min.json`  除去换行、空格的数据 <kbd>175kb</kbd>

## 二、例子
Element Cascader 使用实例

![image](https://user-images.githubusercontent.com/12215982/190945900-003065bd-0674-4506-b757-373bdce6f4d3.png)

```html
<el-cascader :options="provinceData"/>
```

```js
import provinceElement from 'province-element-min.json'

export default {
    name: "ProvinceData",
    data() {
        provinceElement
    }
}
```

## 三、如何从 [ProvinceJson](https://github.com/getActivity/ProvinceJson) 到 Element 可用数据

```js
import province from 'ProvinceJson.json'

this.provinceData = province.map(province => {
                return {
                    value: province.name,
                    label: province.name,
                    children: province.city.map(city => {
                        return {
                            value: city.name,
                            label: city.name,
                            children: city.area.map(area => {
                                return {
                                    value: area,
                                    label: area,
                                }
                            })
                        }
                    })
                }
            })

```
