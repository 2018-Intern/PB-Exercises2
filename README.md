# PB-Exercises2

## SQL Retrieve Arguments + Update Properties

![展示](https://github.com/2018-Intern/PB-Exercises2/blob/master/exercises_2.png)

* SQL Connect 資料庫連線
```
//Connect Button Clicked Event
  dw_search.settransobject(SQLCA) 
```

* SQL Retrieve Arguments 定義參數的類型和名稱，可用來查詢資料使用
```
//查詢按鈕 Clicked Event
 
 string dp_code, dp_name, emp_name, emp_eg_name, emp_tex
 
 dp_code = sle_dp_code.text + "%" //部門代碼
 dp_name = sle_dp_name.text + "%" //部門名稱
 emp_name = sle_emp_name.text + "%" //員工姓名(中)
 emp_eg_name = sle_emp_eg_name.text + "%" //員工姓名(英)
 emp_tex = sle_emp_tex.text + "%" //員工分機(Tex)
 
 dw_search.retrieve(dp_code,dp_name,emp_name,emp_eg_name,emp_tex) //根據Retrieve Arguments所定義的參數進行條件搜索(在此sql語法使用like方式)
 
```

* SQL Update Properties 更新屬性
 > 可至Rows->Update Properties設定
 
 ![參考示意圖](https://github.com/2018-Intern/PB-Exercises2/blob/master/update%20properties.png)
```
//修改按鈕 Clicked Event
//可修改員工姓名(中)

  if dw_search.update() = 1 then
    Commit Using SQLCA;
  else 
    Rollback Using SQLCA;
  end if
```


