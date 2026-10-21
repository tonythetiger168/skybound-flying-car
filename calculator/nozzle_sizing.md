# 噴嘴尺寸鏈計算常數(nozzle sizing chain)

## 氣體常數(N2, 300 K)
gamma = 1.4
R     = 296.8 J/(kg·K)
ff    = sqrt(gamma/(R*T)) * (1+(gamma-1)/2)^(-(gamma+1)/(2(gamma-1))) = 2.295e-3

## 推導鏈
F   = m * g0                      # 總懸浮推力
Fn  = F / N                       # 單嘴推力
At  = Fn / (Cf * Pc)              # 喉部面積  (Cf = 1.55)
Dt  = 2 * sqrt(At / pi)           # 喉部直徑
md  = ff * At * Pc * N            # 總質量流率(與 Pc 無關)
AeAt= isentropic(Pe/Pc)           # 膨脹比(Pc=150 bar → 10.5)
De  = Dt * sqrt(AeAt)             # 出口直徑
mp  = md * t * 1.15               # 燃料量(含 15% 餘量)
n   = ceil(mp / 12.5)             # 50 L / 300 bar 氣瓶數

## 基準點(m=1750 kg, N=8, Pc=150 bar, t=6 s)
F=17.2 kN · Dt=10.8 mm · De=35 mm · mdot=25.4 kg/s · prop=170 kg · 13 瓶

## 推進劑 isp 對照
N2 冷氣體 69 s | H2O2 單組元 145 s | H2O2/煤油 290 s | N2O/HTPB 230 s
