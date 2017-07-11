# Stomatal Conductance Modeling Exercise:  

On Dropbox, you will find a dataset containing meteorological observations and tower-derived GPP estimates collected at MMSF during the course of a severe drought occurring in 2012.  For the purposes of this exercise, the data are limited to midday (i.e. hour 1300) values. Use the data to generate estimates of stomatal conductance using the Leuning model, and plant hydraulic model, and the Medlyn optimality model.  As a reminder, here are the model forms, and some suggested parameter values.

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
$$pgh$$ = 0.3 (appropriate for a 30-m-tall tree)     
Assume
constant $$\Psi_L$$ = -1.8 MPa (isohydric species)