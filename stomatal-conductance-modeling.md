# Stomatal Conductance Modeling Exercise:

Below is a dataset containing meteorological observations and tower-derived GPP estimates collected at MMSF during the course of a severe drought occurring in 2012.

```
DOY    Hour    VPD (kPa)    SWP (Mpa)    VWC (m3/m3)    Par (umol/m2/s)    CO2 (ppm)    GPP (umol/m2/s)    
161.00    13.00    1.78    -0.31    24.16    1581.51    378.88    31.17    
162.00    13.00    0.81    -0.40    22.18    1039.02    393.49    26.87    
163.00    13.00    2.19    -0.35    23.29    1981.02    391.32    14.06    
164.00    13.00    1.65    -0.37    22.79    1959.24    390.29    28.01    
165.00    13.00    2.28    -0.40    22.08    1975.11    386.57    21.81    
166.00    13.00    2.61    -0.43    21.51    1964.63    388.04    17.56    
167.00    13.00    2.32    -0.46    21.06    1921.93    384.74    20.38    
168.00    13.00    1.34    -0.49    20.65    1620.87    392.81    20.75    
169.00    13.00    2.08    -0.53    20.05    1912.18    385.83    22.01    
170.00    13.00    2.28    -0.57    19.51    1942.83    389.73    19.74    
171.00    13.00    2.51    -0.63    18.85    1817.14    390.25    19.51    
172.00    13.00    2.51    -0.67    18.37    1718.25    388.63    20.61    
173.00    13.00    2.37    -0.71    17.99    2004.02    390.08    17.98    
174.00    13.00    2.53    -0.76    17.61    1597.01    384.12    26.28    
175.00    13.00    2.72    -0.80    17.27    1151.81    382.42    22.52    
176.00    13.00    2.40    -0.86    16.83    1974.86    389.35    17.76    
177.00    13.00    2.02    -0.90    16.54    1992.69    389.01    12.18    
178.00    13.00    2.58    -0.96    16.12    1976.11    386.41    16.60    
179.00    13.00    3.77    -1.03    15.74    1945.17    386.67    7.43    
180.00    13.00    3.20    -1.08    15.48    1858.93    386.64    16.02    
181.00    13.00    3.29    -1.12    15.26    1815.67    389.95    12.42    
182.00    13.00    2.84    -1.15    15.00    1679.99    394.88    19.59    
183.00    13.00    2.91    -1.21    14.83    1743.00    393.03    19.10    
184.00    13.00    2.42    -1.24    14.66    1782.24    395.40    20.37    
185.00    13.00    3.41    -1.29    14.47    1846.70    399.83    12.69    
186.00    13.00    4.39    -1.34    14.26    1653.94    397.45    11.65    
187.00    13.00    4.14    -1.38    14.09    1599.68    392.84    8.08    
188.00    13.00    4.19    -1.41    13.99    726.34    392.89    7.05    
189.00    13.00    2.08    -1.41    14.00    183.91    402.59    NaN    
190.00    13.00    2.65    -1.45    13.84    1751.20    383.80    17.21    
191.00    13.00    3.23    -1.51    13.64    1964.57    385.53    13.61    
192.00    13.00    3.03    -1.54    13.54    2000.73    384.07    16.73    
193.00    13.00    3.13    -1.59    13.37    1614.61    384.63    11.51    
194.00    13.00    1.91    -1.60    13.35    1801.13    396.36    23.55    
195.00    13.00    0.89    -1.58    13.40    1973.77    404.49    21.15    
196.00    13.00    1.96    -1.62    13.29    1807.26    398.74    14.46    
197.00    13.00    2.14    -1.65    13.19    832.07    400.72    9.93    
198.00    13.00    2.52    -1.70    13.05    1703.59    398.55    12.63    
199.00    13.00    2.94    -1.70    13.04    1531.01    397.72    11.89
```

For the purposes of this exercise, the data are limited to midday \(i.e. hour 1300\) values. Use the data to generate estimates of stomatal conductance using the Leuning model, and plant hydraulic model, and the Medlyn optimality model.  As a reminder, here are the model forms, and some suggested parameter values.

Use the data to generate estimates of stomatal conductance using the Leuning model, and plant hydraulic model, and the Medlyn optimality model.  As a reminder, here are the model forms, and some suggested parameter values:

### Leuning

$$ g_s = \frac{m_2 A}{s_s - \Gamma}(1 + \frac{D}{D_o})^{-1} + b_2 $$

Let:  
$$D_o$$ = 1.1 kPa  
$$b_2$$ = .001 mol/m2/s  
$$m_2$$ = 6.5 dimensionless  
$$\Gamma$$ = 50 ppm

### Hydraulic Model

$$g_s = \frac{K(\Psi_s - \Psi_L -pgh)}{VPD}$$

Let:  
$$K$$ = 0.3 mol/m2/s  
$$pgh$$ = 0.3 \(appropriate for a 30-m-tall tree\)  
Assume:  
constant $$\Psi_L$$ = -1.8 MPa \(isohydric species\)

### Optimality Model

$$g_s^* \approx g_0 + 1.6(1+ \frac{g_1}{\sqrt{D}})\frac{A}{C_a}$$

Let:  
$$g_0$$ = .001 mol/m2/s  
$$g_1$$ = 2

