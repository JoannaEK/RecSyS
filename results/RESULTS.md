### promt_0 / promt_1: финальные модели

| версия | horizon | поиск | признаков | ROC | PR |
|---|---|---|---|---|---|
| v1_grid5_h7 | 7 | grid5 | 4 | 0.994585 | 0.971874 |
| v2_grid5_h14 | 14 | grid5 | 4 | 0.995995 | 0.979209 |
| v3_grid10_h14 | 14 | grid10 | 4 | 0.995376 | 0.976295 |
| v4_grid10_exp4_h14 | 14 | grid10_exp4 | 4 | 0.996079 | 0.980781 |
| v5_stoch_fixed10_h14 | 14 | stoch_fixed10 | 8 | 0.963118 | 0.856963 |
| v6_stoch_adaptive_h14 | 14 | stoch_adaptive | 8 | 0.964228 | 0.856423 |
| v7_mean_exp3_h14 | 14 | mean_then_exp3 | 8 | 0.968993 | 0.871983 |
| v8_perfeature_h14 | 14 | perfeature_adaptive | 19 | 0.966037 | 0.864436 |

Признаки финальных моделей:

| версия | признаки (оптимальное окно, дней) |
|---|---|
| v1_grid5_h7 | user_tx_cnt (n=7); user_avg_active_day_gap (n=719); user_avg_tx (n=7); vi_tx_cnt (q=7) |
| v2_grid5_h14 | user_tx_cnt (n=7); user_avg_active_day_gap (n=719); user_avg_tx (n=7); vi_tx_cnt (q=7) |
| v3_grid10_h14 | user_tx_cnt (n=7); user_avg_active_day_gap (n=86); user_avg_tx (n=7); vi_tx_cnt (q=7) |
| v4_grid10_exp4_h14 | user_tx_cnt (n=27); user_avg_active_day_gap (n=76); user_avg_tx (n=7); vi_tx_cnt (q=7) |
| v5_stoch_fixed10_h14 | user_tx_cnt (n=343); user_avg_active_day_gap (n=353); user_avg_tx (n=363); item_tx_cnt (m=363); item_avg_active_day_gap (m=353); item_repeat_purchase_rate (m=363); item_avg_tx (m=363); vi_tx_cnt (q=353) |
| v6_stoch_adaptive_h14 | user_tx_cnt (n=443); user_avg_active_day_gap (n=363); user_avg_tx (n=283); item_tx_cnt (m=363); item_avg_active_day_gap (m=403); item_repeat_purchase_rate (m=283); item_avg_tx (m=323); vi_tx_cnt (q=443) |
| v7_mean_exp3_h14 | user_tx_cnt (n=363); user_avg_active_day_gap (n=363); user_avg_tx (n=493); item_tx_cnt (m=333); item_avg_active_day_gap (m=323); item_repeat_purchase_rate (m=363); item_avg_tx (m=283); vi_tx_cnt (q=243) |
| v8_perfeature_h14 | user_tx_cnt (n=443); user_avg_active_day_gap (n=443); user_avg_tx (n=363); item_tx_cnt (m=363); item_avg_active_day_gap (m=363); item_repeat_purchase_rate (m=443); item_avg_tx (m=363); cat_tx_cnt (k=443); cat_avg_active_day_gap (k=363); cat_repeat_purchase_rate (k=283); cat_avg_tx (k=363); vcat_tx_cnt (x=363); vcat_avg_active_day_gap (x=363); vcat_repeat_purchase_rate (x=283); vcat_avg_tx (x=363); vi_tx_cnt (q=283); vc_tx_cnt (s=363); ic_tx_cnt (z=363); ii_co_purchase (u=363) |

### promt_2: long_grid_search

ROC = **0.9919**, PR = **0.9583**, итераций: 3, horizon = 7.

| признак | групповой параметр | оптимальное окно, дней |
|---|---|---|
| user_avg_active_day_gap | n | 719 |
| vi_tx_cnt | q | 7 |

### promt_3: short_stochastic_search на подвыборках

| способ | метод | выборка | пользователей | добавлено | пар | признаков | ROC (подвыборка) | PR (подвыборка) | ROC (полный) | PR (полный) |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | uniform_1pct | 0 | 59 | 0 | 60 | 3 | 0.9 | 0.5 | 0.932675 | 0.751111 |
| 1 | uniform_1pct | 1 | 59 | 0 | 440 | 8 | 0.998413 | 0.994444 | 0.974209 | 0.902416 |
| 1 | uniform_1pct | 2 | 59 | 0 | 530 | 8 | 1.0 | 1.0 | 0.967639 | 0.886595 |
| 2 | typical_top10_uniform | 0 | 42 | 0 | 70 | 19 | 1.0 | 1.0 | 0.966758 | 0.884758 |
| 2 | typical_top10_uniform | 1 | 71 | 29 | 75 | 3 | 0.916667 | 0.833333 | 0.929051 | 0.747012 |
| 2 | typical_top10_uniform | 2 | 42 | 0 | 85 | 3 | 1.0 | 1.0 | 0.920743 | 0.734035 |
| 3 | typical_weighted | 0 | 62 | 15 | 85 | 1 | 1.0 | 1.0 | 0.927124 | 0.71749 |
| 3 | typical_weighted | 1 | 62 | 21 | 85 | 1 | 1.0 | 1.0 | 0.927124 | 0.71749 |
| 3 | typical_weighted | 2 | 62 | 19 | 85 | 3 | 1.0 | 1.0 | 0.924112 | 0.739649 |
