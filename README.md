# cs-form-mtn-006-vs2022

- ### Enter キーを TAB キーとして使用する
```cs
// *****************************************
// ( フォームの KeyPreview : True )
// *****************************************
private void Form1_KeyPress(object sender, KeyPressEventArgs e)
{
    if (e.KeyChar == ControlChars.Cr)
    {
        if ((Control.ModifierKeys & Keys.Shift) == Keys.Shift)
        {
            this.SelectNextControl(this.ActiveControl, false, true, true, true);

        }
        else
        {
            this.SelectNextControl(this.ActiveControl, true, true, true, true);
        }
        e.Handled = true;
    }
}
```

- ### 入力チェック( close ボタンの考慮 )
  - #### Validating でチェック
  - #### Validated で編集

![image](https://github.com/winofsql/cs-form-mtn-006-vs2022/assets/1501327/6f57f827-efac-4b89-9a1a-830672a3e5ec)

![image](https://github.com/winofsql/cs-form-mtn-006-vs2022/assets/1501327/4517b6f0-c218-40eb-aa51-18c5d23d1723)

![image](https://github.com/winofsql/cs-form-mtn-006-vs2022/assets/1501327/e0be425a-8936-40ae-acf5-6dabd122d9dd)
