#self-taught 
Un parametro è una variabile float32, occupa quindi 32bit, 4 byte.
Un modello da 7B parametri (7 miliardi) necessita quindi di $7bln \times 4bytes=28bln \ byte$ che sono circa $28GB$.
Se si caricano invece in float16, dimezziamo lo spazio necessario (e anche l'accuratezza).
I modelli solitamente sono a 8bit, quindi 7B sono 8 gb circa.
# How fast should tokens be generated
Studies suggest that a confortable speed for ai/human interaction is 7tokens/s, while 13t/s is too fast for most users.
# Modelli papabili
_Qwen 2.5 32B is considered a great model for coding, and runs on one 24GB GPU. However, 70B are significantly more intelligent, so I would suggest using Qwen 2.5 72B, and similar models_.
llama-cpp-python Llama-2-7b-chat.Q4_0.gguf attorno ai 21T/s su m3 pro
- llama.cpp inference fast on apple silicon
- ollama is a wrapper of llama.cpp
- mlx is developed by apple, as fast as llama.cpp/ollama
# Quantization
https://github.com/ggerganov/llama.cpp/discussions/2094
```
Allowed quantization types:
   2  or  Q4_0   :  3.50G, +0.2499 ppl @ 7B - small, very high quality loss - legacy, prefer using Q3_K_M
   3  or  Q4_1   :  3.90G, +0.1846 ppl @ 7B - small, substantial quality loss - legacy, prefer using Q3_K_L
   8  or  Q5_0   :  4.30G, +0.0796 ppl @ 7B - medium, balanced quality - legacy, prefer using Q4_K_M
   9  or  Q5_1   :  4.70G, +0.0415 ppl @ 7B - medium, low quality loss - legacy, prefer using Q5_K_M
  10  or  Q2_K   :  2.67G, +0.8698 ppl @ 7B - smallest, extreme quality loss - not recommended
  12  or  Q3_K   : alias for Q3_K_M
  11  or  Q3_K_S :  2.75G, +0.5505 ppl @ 7B - very small, very high quality loss
  12  or  Q3_K_M :  3.06G, +0.2437 ppl @ 7B - very small, very high quality loss
  13  or  Q3_K_L :  3.35G, +0.1803 ppl @ 7B - small, substantial quality loss
  15  or  Q4_K   : alias for Q4_K_M
  14  or  Q4_K_S :  3.56G, +0.1149 ppl @ 7B - small, significant quality loss
  15  or  Q4_K_M :  3.80G, +0.0535 ppl @ 7B - medium, balanced quality - *recommended*
  17  or  Q5_K   : alias for Q5_K_M
  16  or  Q5_K_S :  4.33G, +0.0353 ppl @ 7B - large, low quality loss - *recommended*
  17  or  Q5_K_M :  4.45G, +0.0142 ppl @ 7B - large, very low quality loss - *recommended*
  18  or  Q6_K   :  5.15G, +0.0044 ppl @ 7B - very large, extremely low quality loss
   7  or  Q8_0   :  6.70G, +0.0004 ppl @ 7B - very large, extremely low quality loss - not recommended
   1  or  F16    : 13.00G              @ 7B - extremely large, virtually no quality loss - not recommended
   0  or  F32    : 26.00G              @ 7B - absolutely huge, lossless - not recommended
```