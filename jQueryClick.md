```js
//当用户勾上“全选”时，自动选中所有语言，并把“全选”变成“全不选”；
//当用户去掉“全不选”时，自动不选中所有语言；
function constant_selectAll() {
  selectAll.prop("checked", true);
  selectAllLabel.hide();
  deselectAllLabel.show();
}

function constant_deselectAll() {
  deselectAllLabel.hide();
  selectAllLabel.show();
}

function constant_langsChange() {
  if (langs.filter(":checked").length == langs.length) {
    selectAll.prop("checked", true);
    constant_selectAll();
  } else {
    selectAll.prop("checked", false);
    constant_deselectAll();
  }
}

selectAll.click(function() {
  if (selectAll.is(":checked")) {
    langs.prop("checked", true);
    constant_selectAll();
  } else {
    langs.prop("checked", false);
    constant_deselectAll();
  }
});

//当用户点击“反选”时，自动把所有语言状态反转（选中的变为未选，未选//的变为选中）；

invertSelect.click(function() {
  langs.map(function() {
    let newChecked = !$(this).is(":checked");
    console.log(newChecked);
    $(this).prop("checked", newChecked);
    constant_langsChange();
  });
});

//当用户把所有语言都手动勾上时，“全选”被自动勾上，并变为“全不选”；
//当用户手动去掉选中至少一种语言时，“全不选”自动被去掉选中，并变为//“全选”。

langs.click(function() {
  constant_langsChange();
});
```
