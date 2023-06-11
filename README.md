# cs-form-mtn-006-vs2022

- ### Enter キーを TAB キーとして使用する
```cs
// *****************************************
// ( フォームの KeyPreview : True )
// *****************************************
private void Form1_KeyPress(object sender, KeyPressEventArgs e)
{
    if (e.KeyChar == (char)Keys.Enter)
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

```cs
// *****************************************
// リアルタイム入力チェック
// *****************************************
private void 社員コード_Validating(object sender, System.ComponentModel.CancelEventArgs e)
{
    if (this.ActiveControl != this.社員コード)
    {
        // 数字チェック
        if (!Regex.IsMatch(this.社員コード.Text, @"^[0-9]+$"))
        {
            e.Cancel = true;
            MessageBox.Show("数字を入力してください");
            this.社員コード.SelectAll();
            return;
        }

        // 文字列長チェック
        if (this.社員コード.Text.Length > 4)
        {
            e.Cancel = true;
            MessageBox.Show("4桁以内で入力してください");
            this.社員コード.SelectAll();
            return;
        }
    }
}

private void 社員コード_Validated(object sender, EventArgs e)
{
    if (this.ActiveControl != this.社員コード)
    {
        // 入力チェック終了後の処理
        this.社員コード.Text = $"{Int32.Parse(this.社員コード.Text):0000}";

    }
}
```
