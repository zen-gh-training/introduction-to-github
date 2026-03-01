{%- set all_passed = (results_table | selectattr("passed") | length) == (results_table | length) %}
{%- if all_passed %}

## ステップ {{ step_number }} - 合格 ✅

{%- else %}

## ステップ {{ step_number }} - 不合格 ❌

{%- endif %}

{%- if all_passed %}
<img src="https://octodex.github.com/images/inflatocat.png" align="right" height="150px" alt="ステップ合格を示す Inflatocat の画像" />
{%- else %}

<img src="https://octodex.github.com/images/spidertocat.png" align="right" height="100px" alt="ステップ不合格を示す Spidertocat の画像" />
いくつかのチェックに失敗しました。以下の結果を確認して再度試してください。

原因を見つけて直してみましょう。
{%- endif %}

| ステータス | 説明 |
| ------ | ----------- |

{%- for row in results_table %}
| {% if row.passed -%}✅ - 合格{%- else -%}❌ - 不合格{%- endif %} | {{ row.description }} |
{%- endfor %}

{%- if tips and tips.length %}

### ヒント

{%- for tip in tips %}

- {{ tip }}
  {%- endfor %}

{%- endif %}