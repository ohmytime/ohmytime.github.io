# TRX收发器结构


TRX (Transceiver) 是收发机的核心部分。从代码中可以看到TRX相关的菜单设置：  
&lt;!--more--&gt;

{{&lt; mermaid &gt;}}
graph LR
    A[TRX主结构] --&gt; B[VFO设置]
    A --&gt; C[频率控制]
    A --&gt; D[音频处理]
    A --&gt; E[滤波器]
    A --&gt; F[校准数据]
    A --&gt; G[WiFi设置]

    B --&gt; B1[VFO_A]
    B --&gt; B2[VFO_B]
    B1 --&gt; B11[频率Freq]
    B1 --&gt; B12[模式Mode]
    B1 --&gt; B13[滤波器Filter]
    
    C --&gt; C1[频率步进STEP]
    C --&gt; C2[RIT/XIT]
    C --&gt; C3[波段设置]
    
    D --&gt; D1[音量Volume]
    D --&gt; D2[均衡器EQ]
    D --&gt; D3[AGC控制]
    
    E --&gt; E1[低通LPF]
    E --&gt; E2[高通HPF]
    E --&gt; E3[带通BPF]
    
    F --&gt; F1[SWR校准]
    F --&gt; F2[功率校准]
    F --&gt; F3[S表校准]

{{&lt; /mermaid &gt;}}

---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/trx%E6%94%B6%E5%8F%91%E5%99%A8%E7%BB%93%E6%9E%84/  

