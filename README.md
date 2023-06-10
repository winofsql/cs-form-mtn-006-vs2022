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
