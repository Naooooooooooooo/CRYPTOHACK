# FAVORITE BYTE

The challenge gives us a hex string

>73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d

Telling that the hidden data is XORed with a single byte

A single byte contains 8 bits, so there are 256 cases, we can brute force it

```py
a = '73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d'
a = bytes.fromhex(a)
for i in range(256):
    print(i, end = ' ')
    print(bytes(b ^ i for b in a))
```

The output:
```
0 b"sbi`d\x7fk h! O!%O}iOv$f eb!'#Ori'um"
1 b'rchae~j!i !N $N|hNw%g!dc &"Nsh&tl'
2 b'q`kbf}i"j#"M#\'M\x7fkMt&d"g`#%!Mpk%wo'
3 b'pajcg|h#k"#L"&L~jLu\'e#fa"$ Lqj$vn'
4 b"wfmd`{o$l%$K%!KymKr b$af%#'Kvm#qi"
5 b'vgleazn%m$%J$ JxlJs!c%`g$"&Jwl"ph'
6 b'udofbym&n\'&I\'#I{oIp"`&cd\'!%Ito!sk'
7 b'tengcxl\'o&\'H&"HznHq#a\'be& $Hun rj'
8 b'{jahlwc(`)(G)-GuaG~,n(mj)/+Gza/}e'
9 b'zk`imvb)a()F(,Ft`F\x7f-o)lk(.*F{`.|d'
10 b'yhcjnua*b+*E+/EwcE|.l*oh+-)Exc-\x7fg'
11 b'xibkot`+c*+D*.DvbD}/m+ni*,(Dyb,~f'
12 b'\x7fnelhsg,d-,C-)CqeCz(j,in-+/C~e+ya'
13 b'~odmirf-e,-B,(BpdB{)k-ho,*.B\x7fd*x`'
14 b'}lgnjqe.f/.A/+AsgAx*h.kl/)-A|g){c'
15 b'|mfokpd/g./@.*@rf@y+i/jm.(,@}f(zb'
16 b'crypto{0x10_15_my_f4v0ur173_by7e}'
17 b'bsxqunz1y01^04^lx^g5w1ts062^cx6d|'
18 b'ap{rvmy2z32]37]o{]d6t2wp351]`{5g\x7f'
19 b'`qzswlx3{23\\26\\nz\\e7u3vq240\\az4f~'
20 b'gv}tpk\x7f4|54[51[i}[b0r4qv537[f}3ay'
21 b'fw|uqj~5}45Z40Zh|Zc1s5pw426Zg|2`x'
22 b'et\x7fvri}6~76Y73Yk\x7fY`2p6st715Yd\x7f1c{'
23 b'du~wsh|7\x7f67X62Xj~Xa3q7ru604Xe~0bz'
24 b'kzqx|gs8p98W9=WeqWn<~8}z9?;Wjq?mu'
25 b'j{py}fr9q89V8<VdpVo=\x7f9|{8>:Vkp>lt'
26 b'ixsz~eq:r;:U;?UgsUl>|:\x7fx;=9Uhs=ow'
27 b'hyr{\x7fdp;s:;T:>TfrTm?};~y:<8Tir<nv'
28 b'o~u|xcw<t=<S=9SauSj8z<y~=;?Snu;iq'
29 b'n\x7ft}ybv=u<=R<8R`tRk9{=x\x7f<:>Rot:hp'
30 b'm|w~zau>v?>Q?;QcwQh:x>{|?9=Qlw9ks'
31 b'l}v\x7f{`t?w>?P>:PbvPi;y?z}>8<Pmv8jr'
32 b'SBI@D_K\x00H\x01\x00o\x01\x05o]IoV\x04F\x00EB\x01\x07\x03oRI\x07UM'
33 b'RCHAE^J\x01I\x00\x01n\x00\x04n\\HnW\x05G\x01DC\x00\x06\x02nSH\x06TL'
34 b'Q@KBF]I\x02J\x03\x02m\x03\x07m_KmT\x06D\x02G@\x03\x05\x01mPK\x05WO'
35 b'PAJCG\\H\x03K\x02\x03l\x02\x06l^JlU\x07E\x03FA\x02\x04\x00lQJ\x04VN'
36 b'WFMD@[O\x04L\x05\x04k\x05\x01kYMkR\x00B\x04AF\x05\x03\x07kVM\x03QI'
37 b'VGLEAZN\x05M\x04\x05j\x04\x00jXLjS\x01C\x05@G\x04\x02\x06jWL\x02PH'
38 b'UDOFBYM\x06N\x07\x06i\x07\x03i[OiP\x02@\x06CD\x07\x01\x05iTO\x01SK'
39 b'TENGCXL\x07O\x06\x07h\x06\x02hZNhQ\x03A\x07BE\x06\x00\x04hUN\x00RJ'
40 b'[JAHLWC\x08@\t\x08g\t\rgUAg^\x0cN\x08MJ\t\x0f\x0bgZA\x0f]E'
41 b'ZK@IMVB\tA\x08\tf\x08\x0cfT@f_\rO\tLK\x08\x0e\nf[@\x0e\\D'
42 b'YHCJNUA\nB\x0b\ne\x0b\x0feWCe\\\x0eL\nOH\x0b\r\teXC\r_G'
43 b'XIBKOT@\x0bC\n\x0bd\n\x0edVBd]\x0fM\x0bNI\n\x0c\x08dYB\x0c^F'
44 b'_NELHSG\x0cD\r\x0cc\r\tcQEcZ\x08J\x0cIN\r\x0b\x0fc^E\x0bYA'
45 b'^ODMIRF\rE\x0c\rb\x0c\x08bPDb[\tK\rHO\x0c\n\x0eb_D\nX@'
46 b']LGNJQE\x0eF\x0f\x0ea\x0f\x0baSGaX\nH\x0eKL\x0f\t\ra\\G\t[C'
47 b'\\MFOKPD\x0fG\x0e\x0f`\x0e\n`RF`Y\x0bI\x0fJM\x0e\x08\x0c`]F\x08ZB'
48 b'CRYPTO[\x10X\x11\x10\x7f\x11\x15\x7fMY\x7fF\x14V\x10UR\x11\x17\x13\x7fBY\x17E]'
49 b'BSXQUNZ\x11Y\x10\x11~\x10\x14~LX~G\x15W\x11TS\x10\x16\x12~CX\x16D\\'
50 b'AP[RVMY\x12Z\x13\x12}\x13\x17}O[}D\x16T\x12WP\x13\x15\x11}@[\x15G_'
51 b'@QZSWLX\x13[\x12\x13|\x12\x16|NZ|E\x17U\x13VQ\x12\x14\x10|AZ\x14F^'
52 b'GV]TPK_\x14\\\x15\x14{\x15\x11{I]{B\x10R\x14QV\x15\x13\x17{F]\x13AY'
53 b'FW\\UQJ^\x15]\x14\x15z\x14\x10zH\\zC\x11S\x15PW\x14\x12\x16zG\\\x12@X'
54 b'ET_VRI]\x16^\x17\x16y\x17\x13yK_y@\x12P\x16ST\x17\x11\x15yD_\x11C['
55 b'DU^WSH\\\x17_\x16\x17x\x16\x12xJ^xA\x13Q\x17RU\x16\x10\x14xE^\x10BZ'
56 b'KZQX\\GS\x18P\x19\x18w\x19\x1dwEQwN\x1c^\x18]Z\x19\x1f\x1bwJQ\x1fMU'
57 b'J[PY]FR\x19Q\x18\x19v\x18\x1cvDPvO\x1d_\x19\\[\x18\x1e\x1avKP\x1eLT'
58 b'IXSZ^EQ\x1aR\x1b\x1au\x1b\x1fuGSuL\x1e\\\x1a_X\x1b\x1d\x19uHS\x1dOW'
59 b'HYR[_DP\x1bS\x1a\x1bt\x1a\x1etFRtM\x1f]\x1b^Y\x1a\x1c\x18tIR\x1cNV'
60 b'O^U\\XCW\x1cT\x1d\x1cs\x1d\x19sAUsJ\x18Z\x1cY^\x1d\x1b\x1fsNU\x1bIQ'
61 b'N_T]YBV\x1dU\x1c\x1dr\x1c\x18r@TrK\x19[\x1dX_\x1c\x1a\x1erOT\x1aHP'
62 b'M\\W^ZAU\x1eV\x1f\x1eq\x1f\x1bqCWqH\x1aX\x1e[\\\x1f\x19\x1dqLW\x19KS'
63 b'L]V_[@T\x1fW\x1e\x1fp\x1e\x1apBVpI\x1bY\x1fZ]\x1e\x18\x1cpMV\x18JR'
64 b'3") $?+`(a`\x0fae\x0f=)\x0f6d&`%"agc\x0f2)g5-'
65 b"2#(!%>*a)`a\x0e`d\x0e<(\x0e7e'a$#`fb\x0e3(f4,"
66 b'1 +"&=)b*cb\rcg\r?+\r4f$b\' cea\r0+e7/'
67 b"0!*#'<(c+bc\x0cbf\x0c>*\x0c5g%c&!bd`\x0c1*d6."
68 b'7&-$ ;/d,ed\x0bea\x0b9-\x0b2`"d!&ecg\x0b6-c1)'
69 b"6',%!:.e-de\nd`\n8,\n3a#e 'dbf\n7,b0("
70 b'5$/&"9-f.gf\tgc\t;/\t0b f#$gae\t4/a3+'
71 b'4%.\'#8,g/fg\x08fb\x08:.\x081c!g"%f`d\x085.`2*'
72 b';*!(,7#h ih\x07im\x075!\x07>l.h-*iok\x07:!o=%'
73 b':+ )-6"i!hi\x06hl\x064 \x06?m/i,+hnj\x06; n<$'
74 b'9(#*.5!j"kj\x05ko\x057#\x05<n,j/(kmi\x058#m?\''
75 b'8)"+/4 k#jk\x04jn\x046"\x04=o-k.)jlh\x049"l>&'
76 b"?.%,(3'l$ml\x03mi\x031%\x03:h*l).mko\x03>%k9!"
77 b'>/$-)2&m%lm\x02lh\x020$\x02;i+m(/ljn\x02?$j8 '
78 b"=,'.*1%n&on\x01ok\x013'\x018j(n+,oim\x01<'i;#"
79 b'<-&/+0$o\'no\x00nj\x002&\x009k)o*-nhl\x00=&h:"'
80 b'#2904/;p8qp\x1fqu\x1f-9\x1f&t6p52qws\x1f"9w%='
81 b'"3815.:q9pq\x1ept\x1e,8\x1e\'u7q43pvr\x1e#8v$<'
82 b"!0;26-9r:sr\x1dsw\x1d/;\x1d$v4r70suq\x1d ;u'?"
83 b' 1:37,8s;rs\x1crv\x1c.:\x1c%w5s61rtp\x1c!:t&>'
84 b'\'6=40+?t<ut\x1buq\x1b)=\x1b"p2t16usw\x1b&=s!9'
85 b"&7<51*>u=tu\x1atp\x1a(<\x1a#q3u07trv\x1a'<r 8"
86 b'%4?62)=v>wv\x19ws\x19+?\x19 r0v34wqu\x19$?q#;'
87 b'$5>73(<w?vw\x18vr\x18*>\x18!s1w25vpt\x18%>p":'
88 b"+:18<'3x0yx\x17y}\x17%1\x17.|>x=:y\x7f{\x17*1\x7f-5"
89 b'*;09=&2y1xy\x16x|\x16$0\x16/}?y<;x~z\x16+0~,4'
90 b")83:>%1z2{z\x15{\x7f\x15'3\x15,~<z?8{}y\x15(3}/7"
91 b'(92;?$0{3z{\x14z~\x14&2\x14-\x7f={>9z|x\x14)2|.6'
92 b'/>5<8#7|4}|\x13}y\x13!5\x13*x:|9>}{\x7f\x13.5{)1'
93 b'.?4=9"6}5|}\x12|x\x12 4\x12+y;}8?|z~\x12/4z(0'
94 b'-<7>:!5~6\x7f~\x11\x7f{\x11#7\x11(z8~;<\x7fy}\x11,7y+3'
95 b',=6?; 4\x7f7~\x7f\x10~z\x10"6\x10){9\x7f:=~x|\x10-6x*2'
96 b'\x13\x02\t\x00\x04\x1f\x0b@\x08A@/AE/\x1d\t/\x16D\x06@\x05\x02AGC/\x12\tG\x15\r'
97 b'\x12\x03\x08\x01\x05\x1e\nA\t@A.@D.\x1c\x08.\x17E\x07A\x04\x03@FB.\x13\x08F\x14\x0c'
98 b'\x11\x00\x0b\x02\x06\x1d\tB\nCB-CG-\x1f\x0b-\x14F\x04B\x07\x00CEA-\x10\x0bE\x17\x0f'
99 b'\x10\x01\n\x03\x07\x1c\x08C\x0bBC,BF,\x1e\n,\x15G\x05C\x06\x01BD@,\x11\nD\x16\x0e'
100 b'\x17\x06\r\x04\x00\x1b\x0fD\x0cED+EA+\x19\r+\x12@\x02D\x01\x06ECG+\x16\rC\x11\t'
101 b'\x16\x07\x0c\x05\x01\x1a\x0eE\rDE*D@*\x18\x0c*\x13A\x03E\x00\x07DBF*\x17\x0cB\x10\x08'
102 b'\x15\x04\x0f\x06\x02\x19\rF\x0eGF)GC)\x1b\x0f)\x10B\x00F\x03\x04GAE)\x14\x0fA\x13\x0b'
103 b'\x14\x05\x0e\x07\x03\x18\x0cG\x0fFG(FB(\x1a\x0e(\x11C\x01G\x02\x05F@D(\x15\x0e@\x12\n'
104 b"\x1b\n\x01\x08\x0c\x17\x03H\x00IH'IM'\x15\x01'\x1eL\x0eH\r\nIOK'\x1a\x01O\x1d\x05"
105 b'\x1a\x0b\x00\t\r\x16\x02I\x01HI&HL&\x14\x00&\x1fM\x0fI\x0c\x0bHNJ&\x1b\x00N\x1c\x04'
106 b'\x19\x08\x03\n\x0e\x15\x01J\x02KJ%KO%\x17\x03%\x1cN\x0cJ\x0f\x08KMI%\x18\x03M\x1f\x07'
107 b'\x18\t\x02\x0b\x0f\x14\x00K\x03JK$JN$\x16\x02$\x1dO\rK\x0e\tJLH$\x19\x02L\x1e\x06'
108 b'\x1f\x0e\x05\x0c\x08\x13\x07L\x04ML#MI#\x11\x05#\x1aH\nL\t\x0eMKO#\x1e\x05K\x19\x01'
109 b'\x1e\x0f\x04\r\t\x12\x06M\x05LM"LH"\x10\x04"\x1bI\x0bM\x08\x0fLJN"\x1f\x04J\x18\x00'
110 b'\x1d\x0c\x07\x0e\n\x11\x05N\x06ON!OK!\x13\x07!\x18J\x08N\x0b\x0cOIM!\x1c\x07I\x1b\x03'
111 b'\x1c\r\x06\x0f\x0b\x10\x04O\x07NO NJ \x12\x06 \x19K\tO\n\rNHL \x1d\x06H\x1a\x02'
112 b'\x03\x12\x19\x10\x14\x0f\x1bP\x18QP?QU?\r\x19?\x06T\x16P\x15\x12QWS?\x02\x19W\x05\x1d'
113 b'\x02\x13\x18\x11\x15\x0e\x1aQ\x19PQ>PT>\x0c\x18>\x07U\x17Q\x14\x13PVR>\x03\x18V\x04\x1c'
114 b'\x01\x10\x1b\x12\x16\r\x19R\x1aSR=SW=\x0f\x1b=\x04V\x14R\x17\x10SUQ=\x00\x1bU\x07\x1f'
115 b'\x00\x11\x1a\x13\x17\x0c\x18S\x1bRS<RV<\x0e\x1a<\x05W\x15S\x16\x11RTP<\x01\x1aT\x06\x1e'
116 b'\x07\x16\x1d\x14\x10\x0b\x1fT\x1cUT;UQ;\t\x1d;\x02P\x12T\x11\x16USW;\x06\x1dS\x01\x19'
117 b'\x06\x17\x1c\x15\x11\n\x1eU\x1dTU:TP:\x08\x1c:\x03Q\x13U\x10\x17TRV:\x07\x1cR\x00\x18'
118 b'\x05\x14\x1f\x16\x12\t\x1dV\x1eWV9WS9\x0b\x1f9\x00R\x10V\x13\x14WQU9\x04\x1fQ\x03\x1b'
119 b'\x04\x15\x1e\x17\x13\x08\x1cW\x1fVW8VR8\n\x1e8\x01S\x11W\x12\x15VPT8\x05\x1eP\x02\x1a'
120 b'\x0b\x1a\x11\x18\x1c\x07\x13X\x10YX7Y]7\x05\x117\x0e\\\x1eX\x1d\x1aY_[7\n\x11_\r\x15'
121 b'\n\x1b\x10\x19\x1d\x06\x12Y\x11XY6X\\6\x04\x106\x0f]\x1fY\x1c\x1bX^Z6\x0b\x10^\x0c\x14'
122 b'\t\x18\x13\x1a\x1e\x05\x11Z\x12[Z5[_5\x07\x135\x0c^\x1cZ\x1f\x18[]Y5\x08\x13]\x0f\x17'
123 b'\x08\x19\x12\x1b\x1f\x04\x10[\x13Z[4Z^4\x06\x124\r_\x1d[\x1e\x19Z\\X4\t\x12\\\x0e\x16'
124 b'\x0f\x1e\x15\x1c\x18\x03\x17\\\x14]\\3]Y3\x01\x153\nX\x1a\\\x19\x1e][_3\x0e\x15[\t\x11'
125 b'\x0e\x1f\x14\x1d\x19\x02\x16]\x15\\]2\\X2\x00\x142\x0bY\x1b]\x18\x1f\\Z^2\x0f\x14Z\x08\x10'
126 b'\r\x1c\x17\x1e\x1a\x01\x15^\x16_^1_[1\x03\x171\x08Z\x18^\x1b\x1c_Y]1\x0c\x17Y\x0b\x13'
127 b'\x0c\x1d\x16\x1f\x1b\x00\x14_\x17^_0^Z0\x02\x160\t[\x19_\x1a\x1d^X\\0\r\x16X\n\x12'
128 b'\xf3\xe2\xe9\xe0\xe4\xff\xeb\xa0\xe8\xa1\xa0\xcf\xa1\xa5\xcf\xfd\xe9\xcf\xf6\xa4\xe6\xa0\xe5\xe2\xa1\xa7\xa3\xcf\xf2\xe9\xa7\xf5\xed'
129 b'\xf2\xe3\xe8\xe1\xe5\xfe\xea\xa1\xe9\xa0\xa1\xce\xa0\xa4\xce\xfc\xe8\xce\xf7\xa5\xe7\xa1\xe4\xe3\xa0\xa6\xa2\xce\xf3\xe8\xa6\xf4\xec'
130 b'\xf1\xe0\xeb\xe2\xe6\xfd\xe9\xa2\xea\xa3\xa2\xcd\xa3\xa7\xcd\xff\xeb\xcd\xf4\xa6\xe4\xa2\xe7\xe0\xa3\xa5\xa1\xcd\xf0\xeb\xa5\xf7\xef'
131 b'\xf0\xe1\xea\xe3\xe7\xfc\xe8\xa3\xeb\xa2\xa3\xcc\xa2\xa6\xcc\xfe\xea\xcc\xf5\xa7\xe5\xa3\xe6\xe1\xa2\xa4\xa0\xcc\xf1\xea\xa4\xf6\xee'
132 b'\xf7\xe6\xed\xe4\xe0\xfb\xef\xa4\xec\xa5\xa4\xcb\xa5\xa1\xcb\xf9\xed\xcb\xf2\xa0\xe2\xa4\xe1\xe6\xa5\xa3\xa7\xcb\xf6\xed\xa3\xf1\xe9'
133 b'\xf6\xe7\xec\xe5\xe1\xfa\xee\xa5\xed\xa4\xa5\xca\xa4\xa0\xca\xf8\xec\xca\xf3\xa1\xe3\xa5\xe0\xe7\xa4\xa2\xa6\xca\xf7\xec\xa2\xf0\xe8'
134 b'\xf5\xe4\xef\xe6\xe2\xf9\xed\xa6\xee\xa7\xa6\xc9\xa7\xa3\xc9\xfb\xef\xc9\xf0\xa2\xe0\xa6\xe3\xe4\xa7\xa1\xa5\xc9\xf4\xef\xa1\xf3\xeb'
135 b'\xf4\xe5\xee\xe7\xe3\xf8\xec\xa7\xef\xa6\xa7\xc8\xa6\xa2\xc8\xfa\xee\xc8\xf1\xa3\xe1\xa7\xe2\xe5\xa6\xa0\xa4\xc8\xf5\xee\xa0\xf2\xea'
136 b'\xfb\xea\xe1\xe8\xec\xf7\xe3\xa8\xe0\xa9\xa8\xc7\xa9\xad\xc7\xf5\xe1\xc7\xfe\xac\xee\xa8\xed\xea\xa9\xaf\xab\xc7\xfa\xe1\xaf\xfd\xe5'
137 b'\xfa\xeb\xe0\xe9\xed\xf6\xe2\xa9\xe1\xa8\xa9\xc6\xa8\xac\xc6\xf4\xe0\xc6\xff\xad\xef\xa9\xec\xeb\xa8\xae\xaa\xc6\xfb\xe0\xae\xfc\xe4'
138 b'\xf9\xe8\xe3\xea\xee\xf5\xe1\xaa\xe2\xab\xaa\xc5\xab\xaf\xc5\xf7\xe3\xc5\xfc\xae\xec\xaa\xef\xe8\xab\xad\xa9\xc5\xf8\xe3\xad\xff\xe7'
139 b'\xf8\xe9\xe2\xeb\xef\xf4\xe0\xab\xe3\xaa\xab\xc4\xaa\xae\xc4\xf6\xe2\xc4\xfd\xaf\xed\xab\xee\xe9\xaa\xac\xa8\xc4\xf9\xe2\xac\xfe\xe6'
140 b'\xff\xee\xe5\xec\xe8\xf3\xe7\xac\xe4\xad\xac\xc3\xad\xa9\xc3\xf1\xe5\xc3\xfa\xa8\xea\xac\xe9\xee\xad\xab\xaf\xc3\xfe\xe5\xab\xf9\xe1'
141 b'\xfe\xef\xe4\xed\xe9\xf2\xe6\xad\xe5\xac\xad\xc2\xac\xa8\xc2\xf0\xe4\xc2\xfb\xa9\xeb\xad\xe8\xef\xac\xaa\xae\xc2\xff\xe4\xaa\xf8\xe0'
142 b'\xfd\xec\xe7\xee\xea\xf1\xe5\xae\xe6\xaf\xae\xc1\xaf\xab\xc1\xf3\xe7\xc1\xf8\xaa\xe8\xae\xeb\xec\xaf\xa9\xad\xc1\xfc\xe7\xa9\xfb\xe3'
143 b'\xfc\xed\xe6\xef\xeb\xf0\xe4\xaf\xe7\xae\xaf\xc0\xae\xaa\xc0\xf2\xe6\xc0\xf9\xab\xe9\xaf\xea\xed\xae\xa8\xac\xc0\xfd\xe6\xa8\xfa\xe2'
144 b'\xe3\xf2\xf9\xf0\xf4\xef\xfb\xb0\xf8\xb1\xb0\xdf\xb1\xb5\xdf\xed\xf9\xdf\xe6\xb4\xf6\xb0\xf5\xf2\xb1\xb7\xb3\xdf\xe2\xf9\xb7\xe5\xfd'
145 b'\xe2\xf3\xf8\xf1\xf5\xee\xfa\xb1\xf9\xb0\xb1\xde\xb0\xb4\xde\xec\xf8\xde\xe7\xb5\xf7\xb1\xf4\xf3\xb0\xb6\xb2\xde\xe3\xf8\xb6\xe4\xfc'
146 b'\xe1\xf0\xfb\xf2\xf6\xed\xf9\xb2\xfa\xb3\xb2\xdd\xb3\xb7\xdd\xef\xfb\xdd\xe4\xb6\xf4\xb2\xf7\xf0\xb3\xb5\xb1\xdd\xe0\xfb\xb5\xe7\xff'
147 b'\xe0\xf1\xfa\xf3\xf7\xec\xf8\xb3\xfb\xb2\xb3\xdc\xb2\xb6\xdc\xee\xfa\xdc\xe5\xb7\xf5\xb3\xf6\xf1\xb2\xb4\xb0\xdc\xe1\xfa\xb4\xe6\xfe'
148 b'\xe7\xf6\xfd\xf4\xf0\xeb\xff\xb4\xfc\xb5\xb4\xdb\xb5\xb1\xdb\xe9\xfd\xdb\xe2\xb0\xf2\xb4\xf1\xf6\xb5\xb3\xb7\xdb\xe6\xfd\xb3\xe1\xf9'
149 b'\xe6\xf7\xfc\xf5\xf1\xea\xfe\xb5\xfd\xb4\xb5\xda\xb4\xb0\xda\xe8\xfc\xda\xe3\xb1\xf3\xb5\xf0\xf7\xb4\xb2\xb6\xda\xe7\xfc\xb2\xe0\xf8'
150 b'\xe5\xf4\xff\xf6\xf2\xe9\xfd\xb6\xfe\xb7\xb6\xd9\xb7\xb3\xd9\xeb\xff\xd9\xe0\xb2\xf0\xb6\xf3\xf4\xb7\xb1\xb5\xd9\xe4\xff\xb1\xe3\xfb'
151 b'\xe4\xf5\xfe\xf7\xf3\xe8\xfc\xb7\xff\xb6\xb7\xd8\xb6\xb2\xd8\xea\xfe\xd8\xe1\xb3\xf1\xb7\xf2\xf5\xb6\xb0\xb4\xd8\xe5\xfe\xb0\xe2\xfa'
152 b'\xeb\xfa\xf1\xf8\xfc\xe7\xf3\xb8\xf0\xb9\xb8\xd7\xb9\xbd\xd7\xe5\xf1\xd7\xee\xbc\xfe\xb8\xfd\xfa\xb9\xbf\xbb\xd7\xea\xf1\xbf\xed\xf5'
153 b'\xea\xfb\xf0\xf9\xfd\xe6\xf2\xb9\xf1\xb8\xb9\xd6\xb8\xbc\xd6\xe4\xf0\xd6\xef\xbd\xff\xb9\xfc\xfb\xb8\xbe\xba\xd6\xeb\xf0\xbe\xec\xf4'
154 b'\xe9\xf8\xf3\xfa\xfe\xe5\xf1\xba\xf2\xbb\xba\xd5\xbb\xbf\xd5\xe7\xf3\xd5\xec\xbe\xfc\xba\xff\xf8\xbb\xbd\xb9\xd5\xe8\xf3\xbd\xef\xf7'
155 b'\xe8\xf9\xf2\xfb\xff\xe4\xf0\xbb\xf3\xba\xbb\xd4\xba\xbe\xd4\xe6\xf2\xd4\xed\xbf\xfd\xbb\xfe\xf9\xba\xbc\xb8\xd4\xe9\xf2\xbc\xee\xf6'
156 b'\xef\xfe\xf5\xfc\xf8\xe3\xf7\xbc\xf4\xbd\xbc\xd3\xbd\xb9\xd3\xe1\xf5\xd3\xea\xb8\xfa\xbc\xf9\xfe\xbd\xbb\xbf\xd3\xee\xf5\xbb\xe9\xf1'
157 b'\xee\xff\xf4\xfd\xf9\xe2\xf6\xbd\xf5\xbc\xbd\xd2\xbc\xb8\xd2\xe0\xf4\xd2\xeb\xb9\xfb\xbd\xf8\xff\xbc\xba\xbe\xd2\xef\xf4\xba\xe8\xf0'
158 b'\xed\xfc\xf7\xfe\xfa\xe1\xf5\xbe\xf6\xbf\xbe\xd1\xbf\xbb\xd1\xe3\xf7\xd1\xe8\xba\xf8\xbe\xfb\xfc\xbf\xb9\xbd\xd1\xec\xf7\xb9\xeb\xf3'
159 b'\xec\xfd\xf6\xff\xfb\xe0\xf4\xbf\xf7\xbe\xbf\xd0\xbe\xba\xd0\xe2\xf6\xd0\xe9\xbb\xf9\xbf\xfa\xfd\xbe\xb8\xbc\xd0\xed\xf6\xb8\xea\xf2'
160 b'\xd3\xc2\xc9\xc0\xc4\xdf\xcb\x80\xc8\x81\x80\xef\x81\x85\xef\xdd\xc9\xef\xd6\x84\xc6\x80\xc5\xc2\x81\x87\x83\xef\xd2\xc9\x87\xd5\xcd'
161 b'\xd2\xc3\xc8\xc1\xc5\xde\xca\x81\xc9\x80\x81\xee\x80\x84\xee\xdc\xc8\xee\xd7\x85\xc7\x81\xc4\xc3\x80\x86\x82\xee\xd3\xc8\x86\xd4\xcc'
162 b'\xd1\xc0\xcb\xc2\xc6\xdd\xc9\x82\xca\x83\x82\xed\x83\x87\xed\xdf\xcb\xed\xd4\x86\xc4\x82\xc7\xc0\x83\x85\x81\xed\xd0\xcb\x85\xd7\xcf'
163 b'\xd0\xc1\xca\xc3\xc7\xdc\xc8\x83\xcb\x82\x83\xec\x82\x86\xec\xde\xca\xec\xd5\x87\xc5\x83\xc6\xc1\x82\x84\x80\xec\xd1\xca\x84\xd6\xce'
164 b'\xd7\xc6\xcd\xc4\xc0\xdb\xcf\x84\xcc\x85\x84\xeb\x85\x81\xeb\xd9\xcd\xeb\xd2\x80\xc2\x84\xc1\xc6\x85\x83\x87\xeb\xd6\xcd\x83\xd1\xc9'
165 b'\xd6\xc7\xcc\xc5\xc1\xda\xce\x85\xcd\x84\x85\xea\x84\x80\xea\xd8\xcc\xea\xd3\x81\xc3\x85\xc0\xc7\x84\x82\x86\xea\xd7\xcc\x82\xd0\xc8'
166 b'\xd5\xc4\xcf\xc6\xc2\xd9\xcd\x86\xce\x87\x86\xe9\x87\x83\xe9\xdb\xcf\xe9\xd0\x82\xc0\x86\xc3\xc4\x87\x81\x85\xe9\xd4\xcf\x81\xd3\xcb'
167 b'\xd4\xc5\xce\xc7\xc3\xd8\xcc\x87\xcf\x86\x87\xe8\x86\x82\xe8\xda\xce\xe8\xd1\x83\xc1\x87\xc2\xc5\x86\x80\x84\xe8\xd5\xce\x80\xd2\xca'
168 b'\xdb\xca\xc1\xc8\xcc\xd7\xc3\x88\xc0\x89\x88\xe7\x89\x8d\xe7\xd5\xc1\xe7\xde\x8c\xce\x88\xcd\xca\x89\x8f\x8b\xe7\xda\xc1\x8f\xdd\xc5'
169 b'\xda\xcb\xc0\xc9\xcd\xd6\xc2\x89\xc1\x88\x89\xe6\x88\x8c\xe6\xd4\xc0\xe6\xdf\x8d\xcf\x89\xcc\xcb\x88\x8e\x8a\xe6\xdb\xc0\x8e\xdc\xc4'
170 b'\xd9\xc8\xc3\xca\xce\xd5\xc1\x8a\xc2\x8b\x8a\xe5\x8b\x8f\xe5\xd7\xc3\xe5\xdc\x8e\xcc\x8a\xcf\xc8\x8b\x8d\x89\xe5\xd8\xc3\x8d\xdf\xc7'
171 b'\xd8\xc9\xc2\xcb\xcf\xd4\xc0\x8b\xc3\x8a\x8b\xe4\x8a\x8e\xe4\xd6\xc2\xe4\xdd\x8f\xcd\x8b\xce\xc9\x8a\x8c\x88\xe4\xd9\xc2\x8c\xde\xc6'
172 b'\xdf\xce\xc5\xcc\xc8\xd3\xc7\x8c\xc4\x8d\x8c\xe3\x8d\x89\xe3\xd1\xc5\xe3\xda\x88\xca\x8c\xc9\xce\x8d\x8b\x8f\xe3\xde\xc5\x8b\xd9\xc1'
173 b'\xde\xcf\xc4\xcd\xc9\xd2\xc6\x8d\xc5\x8c\x8d\xe2\x8c\x88\xe2\xd0\xc4\xe2\xdb\x89\xcb\x8d\xc8\xcf\x8c\x8a\x8e\xe2\xdf\xc4\x8a\xd8\xc0'
174 b'\xdd\xcc\xc7\xce\xca\xd1\xc5\x8e\xc6\x8f\x8e\xe1\x8f\x8b\xe1\xd3\xc7\xe1\xd8\x8a\xc8\x8e\xcb\xcc\x8f\x89\x8d\xe1\xdc\xc7\x89\xdb\xc3'
175 b'\xdc\xcd\xc6\xcf\xcb\xd0\xc4\x8f\xc7\x8e\x8f\xe0\x8e\x8a\xe0\xd2\xc6\xe0\xd9\x8b\xc9\x8f\xca\xcd\x8e\x88\x8c\xe0\xdd\xc6\x88\xda\xc2'
176 b'\xc3\xd2\xd9\xd0\xd4\xcf\xdb\x90\xd8\x91\x90\xff\x91\x95\xff\xcd\xd9\xff\xc6\x94\xd6\x90\xd5\xd2\x91\x97\x93\xff\xc2\xd9\x97\xc5\xdd'
177 b'\xc2\xd3\xd8\xd1\xd5\xce\xda\x91\xd9\x90\x91\xfe\x90\x94\xfe\xcc\xd8\xfe\xc7\x95\xd7\x91\xd4\xd3\x90\x96\x92\xfe\xc3\xd8\x96\xc4\xdc'
178 b'\xc1\xd0\xdb\xd2\xd6\xcd\xd9\x92\xda\x93\x92\xfd\x93\x97\xfd\xcf\xdb\xfd\xc4\x96\xd4\x92\xd7\xd0\x93\x95\x91\xfd\xc0\xdb\x95\xc7\xdf'
179 b'\xc0\xd1\xda\xd3\xd7\xcc\xd8\x93\xdb\x92\x93\xfc\x92\x96\xfc\xce\xda\xfc\xc5\x97\xd5\x93\xd6\xd1\x92\x94\x90\xfc\xc1\xda\x94\xc6\xde'
180 b'\xc7\xd6\xdd\xd4\xd0\xcb\xdf\x94\xdc\x95\x94\xfb\x95\x91\xfb\xc9\xdd\xfb\xc2\x90\xd2\x94\xd1\xd6\x95\x93\x97\xfb\xc6\xdd\x93\xc1\xd9'
181 b'\xc6\xd7\xdc\xd5\xd1\xca\xde\x95\xdd\x94\x95\xfa\x94\x90\xfa\xc8\xdc\xfa\xc3\x91\xd3\x95\xd0\xd7\x94\x92\x96\xfa\xc7\xdc\x92\xc0\xd8'
182 b'\xc5\xd4\xdf\xd6\xd2\xc9\xdd\x96\xde\x97\x96\xf9\x97\x93\xf9\xcb\xdf\xf9\xc0\x92\xd0\x96\xd3\xd4\x97\x91\x95\xf9\xc4\xdf\x91\xc3\xdb'
183 b'\xc4\xd5\xde\xd7\xd3\xc8\xdc\x97\xdf\x96\x97\xf8\x96\x92\xf8\xca\xde\xf8\xc1\x93\xd1\x97\xd2\xd5\x96\x90\x94\xf8\xc5\xde\x90\xc2\xda'
184 b'\xcb\xda\xd1\xd8\xdc\xc7\xd3\x98\xd0\x99\x98\xf7\x99\x9d\xf7\xc5\xd1\xf7\xce\x9c\xde\x98\xdd\xda\x99\x9f\x9b\xf7\xca\xd1\x9f\xcd\xd5'
185 b'\xca\xdb\xd0\xd9\xdd\xc6\xd2\x99\xd1\x98\x99\xf6\x98\x9c\xf6\xc4\xd0\xf6\xcf\x9d\xdf\x99\xdc\xdb\x98\x9e\x9a\xf6\xcb\xd0\x9e\xcc\xd4'
186 b'\xc9\xd8\xd3\xda\xde\xc5\xd1\x9a\xd2\x9b\x9a\xf5\x9b\x9f\xf5\xc7\xd3\xf5\xcc\x9e\xdc\x9a\xdf\xd8\x9b\x9d\x99\xf5\xc8\xd3\x9d\xcf\xd7'
187 b'\xc8\xd9\xd2\xdb\xdf\xc4\xd0\x9b\xd3\x9a\x9b\xf4\x9a\x9e\xf4\xc6\xd2\xf4\xcd\x9f\xdd\x9b\xde\xd9\x9a\x9c\x98\xf4\xc9\xd2\x9c\xce\xd6'
188 b'\xcf\xde\xd5\xdc\xd8\xc3\xd7\x9c\xd4\x9d\x9c\xf3\x9d\x99\xf3\xc1\xd5\xf3\xca\x98\xda\x9c\xd9\xde\x9d\x9b\x9f\xf3\xce\xd5\x9b\xc9\xd1'
189 b'\xce\xdf\xd4\xdd\xd9\xc2\xd6\x9d\xd5\x9c\x9d\xf2\x9c\x98\xf2\xc0\xd4\xf2\xcb\x99\xdb\x9d\xd8\xdf\x9c\x9a\x9e\xf2\xcf\xd4\x9a\xc8\xd0'
190 b'\xcd\xdc\xd7\xde\xda\xc1\xd5\x9e\xd6\x9f\x9e\xf1\x9f\x9b\xf1\xc3\xd7\xf1\xc8\x9a\xd8\x9e\xdb\xdc\x9f\x99\x9d\xf1\xcc\xd7\x99\xcb\xd3'
191 b'\xcc\xdd\xd6\xdf\xdb\xc0\xd4\x9f\xd7\x9e\x9f\xf0\x9e\x9a\xf0\xc2\xd6\xf0\xc9\x9b\xd9\x9f\xda\xdd\x9e\x98\x9c\xf0\xcd\xd6\x98\xca\xd2'
192 b'\xb3\xa2\xa9\xa0\xa4\xbf\xab\xe0\xa8\xe1\xe0\x8f\xe1\xe5\x8f\xbd\xa9\x8f\xb6\xe4\xa6\xe0\xa5\xa2\xe1\xe7\xe3\x8f\xb2\xa9\xe7\xb5\xad'
193 b'\xb2\xa3\xa8\xa1\xa5\xbe\xaa\xe1\xa9\xe0\xe1\x8e\xe0\xe4\x8e\xbc\xa8\x8e\xb7\xe5\xa7\xe1\xa4\xa3\xe0\xe6\xe2\x8e\xb3\xa8\xe6\xb4\xac'
194 b'\xb1\xa0\xab\xa2\xa6\xbd\xa9\xe2\xaa\xe3\xe2\x8d\xe3\xe7\x8d\xbf\xab\x8d\xb4\xe6\xa4\xe2\xa7\xa0\xe3\xe5\xe1\x8d\xb0\xab\xe5\xb7\xaf'
195 b'\xb0\xa1\xaa\xa3\xa7\xbc\xa8\xe3\xab\xe2\xe3\x8c\xe2\xe6\x8c\xbe\xaa\x8c\xb5\xe7\xa5\xe3\xa6\xa1\xe2\xe4\xe0\x8c\xb1\xaa\xe4\xb6\xae'
196 b'\xb7\xa6\xad\xa4\xa0\xbb\xaf\xe4\xac\xe5\xe4\x8b\xe5\xe1\x8b\xb9\xad\x8b\xb2\xe0\xa2\xe4\xa1\xa6\xe5\xe3\xe7\x8b\xb6\xad\xe3\xb1\xa9'
197 b'\xb6\xa7\xac\xa5\xa1\xba\xae\xe5\xad\xe4\xe5\x8a\xe4\xe0\x8a\xb8\xac\x8a\xb3\xe1\xa3\xe5\xa0\xa7\xe4\xe2\xe6\x8a\xb7\xac\xe2\xb0\xa8'
198 b'\xb5\xa4\xaf\xa6\xa2\xb9\xad\xe6\xae\xe7\xe6\x89\xe7\xe3\x89\xbb\xaf\x89\xb0\xe2\xa0\xe6\xa3\xa4\xe7\xe1\xe5\x89\xb4\xaf\xe1\xb3\xab'
199 b'\xb4\xa5\xae\xa7\xa3\xb8\xac\xe7\xaf\xe6\xe7\x88\xe6\xe2\x88\xba\xae\x88\xb1\xe3\xa1\xe7\xa2\xa5\xe6\xe0\xe4\x88\xb5\xae\xe0\xb2\xaa'
200 b'\xbb\xaa\xa1\xa8\xac\xb7\xa3\xe8\xa0\xe9\xe8\x87\xe9\xed\x87\xb5\xa1\x87\xbe\xec\xae\xe8\xad\xaa\xe9\xef\xeb\x87\xba\xa1\xef\xbd\xa5'
201 b'\xba\xab\xa0\xa9\xad\xb6\xa2\xe9\xa1\xe8\xe9\x86\xe8\xec\x86\xb4\xa0\x86\xbf\xed\xaf\xe9\xac\xab\xe8\xee\xea\x86\xbb\xa0\xee\xbc\xa4'
202 b'\xb9\xa8\xa3\xaa\xae\xb5\xa1\xea\xa2\xeb\xea\x85\xeb\xef\x85\xb7\xa3\x85\xbc\xee\xac\xea\xaf\xa8\xeb\xed\xe9\x85\xb8\xa3\xed\xbf\xa7'
203 b'\xb8\xa9\xa2\xab\xaf\xb4\xa0\xeb\xa3\xea\xeb\x84\xea\xee\x84\xb6\xa2\x84\xbd\xef\xad\xeb\xae\xa9\xea\xec\xe8\x84\xb9\xa2\xec\xbe\xa6'
204 b'\xbf\xae\xa5\xac\xa8\xb3\xa7\xec\xa4\xed\xec\x83\xed\xe9\x83\xb1\xa5\x83\xba\xe8\xaa\xec\xa9\xae\xed\xeb\xef\x83\xbe\xa5\xeb\xb9\xa1'
205 b'\xbe\xaf\xa4\xad\xa9\xb2\xa6\xed\xa5\xec\xed\x82\xec\xe8\x82\xb0\xa4\x82\xbb\xe9\xab\xed\xa8\xaf\xec\xea\xee\x82\xbf\xa4\xea\xb8\xa0'
206 b'\xbd\xac\xa7\xae\xaa\xb1\xa5\xee\xa6\xef\xee\x81\xef\xeb\x81\xb3\xa7\x81\xb8\xea\xa8\xee\xab\xac\xef\xe9\xed\x81\xbc\xa7\xe9\xbb\xa3'
207 b'\xbc\xad\xa6\xaf\xab\xb0\xa4\xef\xa7\xee\xef\x80\xee\xea\x80\xb2\xa6\x80\xb9\xeb\xa9\xef\xaa\xad\xee\xe8\xec\x80\xbd\xa6\xe8\xba\xa2'
208 b'\xa3\xb2\xb9\xb0\xb4\xaf\xbb\xf0\xb8\xf1\xf0\x9f\xf1\xf5\x9f\xad\xb9\x9f\xa6\xf4\xb6\xf0\xb5\xb2\xf1\xf7\xf3\x9f\xa2\xb9\xf7\xa5\xbd'
209 b'\xa2\xb3\xb8\xb1\xb5\xae\xba\xf1\xb9\xf0\xf1\x9e\xf0\xf4\x9e\xac\xb8\x9e\xa7\xf5\xb7\xf1\xb4\xb3\xf0\xf6\xf2\x9e\xa3\xb8\xf6\xa4\xbc'
210 b'\xa1\xb0\xbb\xb2\xb6\xad\xb9\xf2\xba\xf3\xf2\x9d\xf3\xf7\x9d\xaf\xbb\x9d\xa4\xf6\xb4\xf2\xb7\xb0\xf3\xf5\xf1\x9d\xa0\xbb\xf5\xa7\xbf'
211 b'\xa0\xb1\xba\xb3\xb7\xac\xb8\xf3\xbb\xf2\xf3\x9c\xf2\xf6\x9c\xae\xba\x9c\xa5\xf7\xb5\xf3\xb6\xb1\xf2\xf4\xf0\x9c\xa1\xba\xf4\xa6\xbe'
212 b'\xa7\xb6\xbd\xb4\xb0\xab\xbf\xf4\xbc\xf5\xf4\x9b\xf5\xf1\x9b\xa9\xbd\x9b\xa2\xf0\xb2\xf4\xb1\xb6\xf5\xf3\xf7\x9b\xa6\xbd\xf3\xa1\xb9'
213 b'\xa6\xb7\xbc\xb5\xb1\xaa\xbe\xf5\xbd\xf4\xf5\x9a\xf4\xf0\x9a\xa8\xbc\x9a\xa3\xf1\xb3\xf5\xb0\xb7\xf4\xf2\xf6\x9a\xa7\xbc\xf2\xa0\xb8'
214 b'\xa5\xb4\xbf\xb6\xb2\xa9\xbd\xf6\xbe\xf7\xf6\x99\xf7\xf3\x99\xab\xbf\x99\xa0\xf2\xb0\xf6\xb3\xb4\xf7\xf1\xf5\x99\xa4\xbf\xf1\xa3\xbb'
215 b'\xa4\xb5\xbe\xb7\xb3\xa8\xbc\xf7\xbf\xf6\xf7\x98\xf6\xf2\x98\xaa\xbe\x98\xa1\xf3\xb1\xf7\xb2\xb5\xf6\xf0\xf4\x98\xa5\xbe\xf0\xa2\xba'
216 b'\xab\xba\xb1\xb8\xbc\xa7\xb3\xf8\xb0\xf9\xf8\x97\xf9\xfd\x97\xa5\xb1\x97\xae\xfc\xbe\xf8\xbd\xba\xf9\xff\xfb\x97\xaa\xb1\xff\xad\xb5'
217 b'\xaa\xbb\xb0\xb9\xbd\xa6\xb2\xf9\xb1\xf8\xf9\x96\xf8\xfc\x96\xa4\xb0\x96\xaf\xfd\xbf\xf9\xbc\xbb\xf8\xfe\xfa\x96\xab\xb0\xfe\xac\xb4'
218 b'\xa9\xb8\xb3\xba\xbe\xa5\xb1\xfa\xb2\xfb\xfa\x95\xfb\xff\x95\xa7\xb3\x95\xac\xfe\xbc\xfa\xbf\xb8\xfb\xfd\xf9\x95\xa8\xb3\xfd\xaf\xb7'
219 b'\xa8\xb9\xb2\xbb\xbf\xa4\xb0\xfb\xb3\xfa\xfb\x94\xfa\xfe\x94\xa6\xb2\x94\xad\xff\xbd\xfb\xbe\xb9\xfa\xfc\xf8\x94\xa9\xb2\xfc\xae\xb6'
220 b'\xaf\xbe\xb5\xbc\xb8\xa3\xb7\xfc\xb4\xfd\xfc\x93\xfd\xf9\x93\xa1\xb5\x93\xaa\xf8\xba\xfc\xb9\xbe\xfd\xfb\xff\x93\xae\xb5\xfb\xa9\xb1'
221 b'\xae\xbf\xb4\xbd\xb9\xa2\xb6\xfd\xb5\xfc\xfd\x92\xfc\xf8\x92\xa0\xb4\x92\xab\xf9\xbb\xfd\xb8\xbf\xfc\xfa\xfe\x92\xaf\xb4\xfa\xa8\xb0'
222 b'\xad\xbc\xb7\xbe\xba\xa1\xb5\xfe\xb6\xff\xfe\x91\xff\xfb\x91\xa3\xb7\x91\xa8\xfa\xb8\xfe\xbb\xbc\xff\xf9\xfd\x91\xac\xb7\xf9\xab\xb3'
223 b'\xac\xbd\xb6\xbf\xbb\xa0\xb4\xff\xb7\xfe\xff\x90\xfe\xfa\x90\xa2\xb6\x90\xa9\xfb\xb9\xff\xba\xbd\xfe\xf8\xfc\x90\xad\xb6\xf8\xaa\xb2'
224 b'\x93\x82\x89\x80\x84\x9f\x8b\xc0\x88\xc1\xc0\xaf\xc1\xc5\xaf\x9d\x89\xaf\x96\xc4\x86\xc0\x85\x82\xc1\xc7\xc3\xaf\x92\x89\xc7\x95\x8d'
225 b'\x92\x83\x88\x81\x85\x9e\x8a\xc1\x89\xc0\xc1\xae\xc0\xc4\xae\x9c\x88\xae\x97\xc5\x87\xc1\x84\x83\xc0\xc6\xc2\xae\x93\x88\xc6\x94\x8c'
226 b'\x91\x80\x8b\x82\x86\x9d\x89\xc2\x8a\xc3\xc2\xad\xc3\xc7\xad\x9f\x8b\xad\x94\xc6\x84\xc2\x87\x80\xc3\xc5\xc1\xad\x90\x8b\xc5\x97\x8f'
227 b'\x90\x81\x8a\x83\x87\x9c\x88\xc3\x8b\xc2\xc3\xac\xc2\xc6\xac\x9e\x8a\xac\x95\xc7\x85\xc3\x86\x81\xc2\xc4\xc0\xac\x91\x8a\xc4\x96\x8e'
228 b'\x97\x86\x8d\x84\x80\x9b\x8f\xc4\x8c\xc5\xc4\xab\xc5\xc1\xab\x99\x8d\xab\x92\xc0\x82\xc4\x81\x86\xc5\xc3\xc7\xab\x96\x8d\xc3\x91\x89'
229 b'\x96\x87\x8c\x85\x81\x9a\x8e\xc5\x8d\xc4\xc5\xaa\xc4\xc0\xaa\x98\x8c\xaa\x93\xc1\x83\xc5\x80\x87\xc4\xc2\xc6\xaa\x97\x8c\xc2\x90\x88'
230 b'\x95\x84\x8f\x86\x82\x99\x8d\xc6\x8e\xc7\xc6\xa9\xc7\xc3\xa9\x9b\x8f\xa9\x90\xc2\x80\xc6\x83\x84\xc7\xc1\xc5\xa9\x94\x8f\xc1\x93\x8b'
231 b'\x94\x85\x8e\x87\x83\x98\x8c\xc7\x8f\xc6\xc7\xa8\xc6\xc2\xa8\x9a\x8e\xa8\x91\xc3\x81\xc7\x82\x85\xc6\xc0\xc4\xa8\x95\x8e\xc0\x92\x8a'
232 b'\x9b\x8a\x81\x88\x8c\x97\x83\xc8\x80\xc9\xc8\xa7\xc9\xcd\xa7\x95\x81\xa7\x9e\xcc\x8e\xc8\x8d\x8a\xc9\xcf\xcb\xa7\x9a\x81\xcf\x9d\x85'
233 b'\x9a\x8b\x80\x89\x8d\x96\x82\xc9\x81\xc8\xc9\xa6\xc8\xcc\xa6\x94\x80\xa6\x9f\xcd\x8f\xc9\x8c\x8b\xc8\xce\xca\xa6\x9b\x80\xce\x9c\x84'
234 b'\x99\x88\x83\x8a\x8e\x95\x81\xca\x82\xcb\xca\xa5\xcb\xcf\xa5\x97\x83\xa5\x9c\xce\x8c\xca\x8f\x88\xcb\xcd\xc9\xa5\x98\x83\xcd\x9f\x87'
235 b'\x98\x89\x82\x8b\x8f\x94\x80\xcb\x83\xca\xcb\xa4\xca\xce\xa4\x96\x82\xa4\x9d\xcf\x8d\xcb\x8e\x89\xca\xcc\xc8\xa4\x99\x82\xcc\x9e\x86'
236 b'\x9f\x8e\x85\x8c\x88\x93\x87\xcc\x84\xcd\xcc\xa3\xcd\xc9\xa3\x91\x85\xa3\x9a\xc8\x8a\xcc\x89\x8e\xcd\xcb\xcf\xa3\x9e\x85\xcb\x99\x81'
237 b'\x9e\x8f\x84\x8d\x89\x92\x86\xcd\x85\xcc\xcd\xa2\xcc\xc8\xa2\x90\x84\xa2\x9b\xc9\x8b\xcd\x88\x8f\xcc\xca\xce\xa2\x9f\x84\xca\x98\x80'
238 b'\x9d\x8c\x87\x8e\x8a\x91\x85\xce\x86\xcf\xce\xa1\xcf\xcb\xa1\x93\x87\xa1\x98\xca\x88\xce\x8b\x8c\xcf\xc9\xcd\xa1\x9c\x87\xc9\x9b\x83'
239 b'\x9c\x8d\x86\x8f\x8b\x90\x84\xcf\x87\xce\xcf\xa0\xce\xca\xa0\x92\x86\xa0\x99\xcb\x89\xcf\x8a\x8d\xce\xc8\xcc\xa0\x9d\x86\xc8\x9a\x82'
240 b'\x83\x92\x99\x90\x94\x8f\x9b\xd0\x98\xd1\xd0\xbf\xd1\xd5\xbf\x8d\x99\xbf\x86\xd4\x96\xd0\x95\x92\xd1\xd7\xd3\xbf\x82\x99\xd7\x85\x9d'
241 b'\x82\x93\x98\x91\x95\x8e\x9a\xd1\x99\xd0\xd1\xbe\xd0\xd4\xbe\x8c\x98\xbe\x87\xd5\x97\xd1\x94\x93\xd0\xd6\xd2\xbe\x83\x98\xd6\x84\x9c'
242 b'\x81\x90\x9b\x92\x96\x8d\x99\xd2\x9a\xd3\xd2\xbd\xd3\xd7\xbd\x8f\x9b\xbd\x84\xd6\x94\xd2\x97\x90\xd3\xd5\xd1\xbd\x80\x9b\xd5\x87\x9f'
243 b'\x80\x91\x9a\x93\x97\x8c\x98\xd3\x9b\xd2\xd3\xbc\xd2\xd6\xbc\x8e\x9a\xbc\x85\xd7\x95\xd3\x96\x91\xd2\xd4\xd0\xbc\x81\x9a\xd4\x86\x9e'
244 b'\x87\x96\x9d\x94\x90\x8b\x9f\xd4\x9c\xd5\xd4\xbb\xd5\xd1\xbb\x89\x9d\xbb\x82\xd0\x92\xd4\x91\x96\xd5\xd3\xd7\xbb\x86\x9d\xd3\x81\x99'
245 b'\x86\x97\x9c\x95\x91\x8a\x9e\xd5\x9d\xd4\xd5\xba\xd4\xd0\xba\x88\x9c\xba\x83\xd1\x93\xd5\x90\x97\xd4\xd2\xd6\xba\x87\x9c\xd2\x80\x98'
246 b'\x85\x94\x9f\x96\x92\x89\x9d\xd6\x9e\xd7\xd6\xb9\xd7\xd3\xb9\x8b\x9f\xb9\x80\xd2\x90\xd6\x93\x94\xd7\xd1\xd5\xb9\x84\x9f\xd1\x83\x9b'
247 b'\x84\x95\x9e\x97\x93\x88\x9c\xd7\x9f\xd6\xd7\xb8\xd6\xd2\xb8\x8a\x9e\xb8\x81\xd3\x91\xd7\x92\x95\xd6\xd0\xd4\xb8\x85\x9e\xd0\x82\x9a'
248 b'\x8b\x9a\x91\x98\x9c\x87\x93\xd8\x90\xd9\xd8\xb7\xd9\xdd\xb7\x85\x91\xb7\x8e\xdc\x9e\xd8\x9d\x9a\xd9\xdf\xdb\xb7\x8a\x91\xdf\x8d\x95'
249 b'\x8a\x9b\x90\x99\x9d\x86\x92\xd9\x91\xd8\xd9\xb6\xd8\xdc\xb6\x84\x90\xb6\x8f\xdd\x9f\xd9\x9c\x9b\xd8\xde\xda\xb6\x8b\x90\xde\x8c\x94'
250 b'\x89\x98\x93\x9a\x9e\x85\x91\xda\x92\xdb\xda\xb5\xdb\xdf\xb5\x87\x93\xb5\x8c\xde\x9c\xda\x9f\x98\xdb\xdd\xd9\xb5\x88\x93\xdd\x8f\x97'
251 b'\x88\x99\x92\x9b\x9f\x84\x90\xdb\x93\xda\xdb\xb4\xda\xde\xb4\x86\x92\xb4\x8d\xdf\x9d\xdb\x9e\x99\xda\xdc\xd8\xb4\x89\x92\xdc\x8e\x96'
252 b'\x8f\x9e\x95\x9c\x98\x83\x97\xdc\x94\xdd\xdc\xb3\xdd\xd9\xb3\x81\x95\xb3\x8a\xd8\x9a\xdc\x99\x9e\xdd\xdb\xdf\xb3\x8e\x95\xdb\x89\x91'
253 b'\x8e\x9f\x94\x9d\x99\x82\x96\xdd\x95\xdc\xdd\xb2\xdc\xd8\xb2\x80\x94\xb2\x8b\xd9\x9b\xdd\x98\x9f\xdc\xda\xde\xb2\x8f\x94\xda\x88\x90'
254 b'\x8d\x9c\x97\x9e\x9a\x81\x95\xde\x96\xdf\xde\xb1\xdf\xdb\xb1\x83\x97\xb1\x88\xda\x98\xde\x9b\x9c\xdf\xd9\xdd\xb1\x8c\x97\xd9\x8b\x93'
255 b'\x8c\x9d\x96\x9f\x9b\x80\x94\xdf\x97\xde\xdf\xb0\xde\xda\xb0\x82\x96\xb0\x89\xdb\x99\xdf\x9a\x9d\xde\xd8\xdc\xb0\x8d\x96\xd8\x8a\x92'
```

We see that at `i = 16`

>16 b'crypto{0x10_15_my_f4v0ur173_by7e}'

That's our flag