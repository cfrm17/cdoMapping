# Mapping CDO2&3 to Risk Equivalent CDO


Mapping CDO2 and CDO3 trades to risk equivalent CDO (RE-CDO) trades can be done by matching the b/e spread a RE-CDO is calculated and taken as the proxy of a target CDO2 or CDO3 trade.  Then the MTM of the CDO2 or CDO3 trade can be calculated using the market observed correlations by finding the MTM of the proxy via index base correlations.

At the present time there is no generally accepted methodology of applying market observed correlation information to a bespoke CDO2 or CDO3 trade. The GSP mapping methodology is similar to the idea of a roughly delta hedging of a CDO2 and CDO3 trade with a CDO trade. The tests have shown that the methodology does capture the most of the market risk of credit spread and correlation if calibrated frequently and has been implemented correctly.

However, we have also indicated that such mapping is not based on a sound theoretical foundation and can only be viewed as an approximation. The approximation is acceptable only when each child mezzanine tranches has very similar risk exposure of correlation and credit. 

The model serves the purpose of finding a proxy CDO for a CDO2 or CDO3 trade by matching b/e spread. The proxy CDO has a collateral pool with the same reference names as that of the CDO2 or CDO3 trade and the notional amount of each name is the average of that of all child CDO pools. It has the same thickness of the tranche as that of the CDO2 or CDO3 trade and its attachment is calculated such that the b/e spread matches that of the CDO2 or CDO3 trade. The MTM of the CDO2 or CDO3 trade can then be calculated using the market observed correlations by finding the MTM of the proxy via index base correlations.

The methodology can be illustrated through the following example. As shown in Figure 1, a CDO2 trade has two child pools with the reference names 8~12 being shared. This CDO2 trade can be mapped to another risk equivalent CDO (RE-CDO) with the pool shown in Fig. 1. In this pool the notional of each reference name is the average of that of two child CDOs.  

 

We define the loss function of the two child pools as

(1) 	 ,

 where    is the loss given default (LGD) for the  reference name and  is the default time. The child CDO trades have the attachment and detachment points   for pool A and   for pool B. Then the loss function of a CDO2 trade with attachment point  and thickness   can be expressed as:

(2)	 ,

and the loss function of RE-CDO reads

 (3)	 

The expected losses of the CDO2 trade and the RE-CDO trade can then have the form

(4)	 

Here the attachment point of this RE-CDO tranche   is unknown. The mapping is to solve this attachment point such that the b/e spread of a CDO2 and a RE-CDO matches.  The following procedure is employed:

1.	Setting correlation be 0.2, find the b/e spread of the CDO2 tranche using the valuation model available in the GSP modelling framework.
2.	Taking the b/e spread calculated in the first step; find the attachment point by using CDO valuation model in reverse.

For CDO3 trades, the exactly same procedure is used except that a CDO3 valuation model (see https://finpricing.com/lib/FiBond.html) is employed instead in the first step. As shown in the Eq.(4), all the complicated structures in the CDO2 and CDO3 trades are simply ignored. However, the value and sensitivities of the CDO2 and CDO3 trades are the functions of these structures. For example, the overlapping effect cannot be captured in the RE-CDO.  This can be elaborated with the following scenarios:

1.	If we assume all reference names have the same credit spread level, two default events in a CDO2 would have six possible cases: both in pool A but not sharing, both in B but not sharing, etc. Each case has a different effect due to the subordination of each child CDO and the overlapping feature. However, it is indistinguishable in the RE-CDO trade and we treat all six cases as one case. 

2.	If we set   and  , then we have 

(5)	 .

We essentially change the CDO2 into a CDO, which has a different loss function from that of the RE-CDO as shown in Eq. (3). We won’t expect that they will have identical risk profile using whatever mapping methodology in this scenario.

3.	If two child CDOs have the same collateral pools  and  , we would write the loss function as

(6)	 

Apparently one is a linear function of loss function and the other is a nonlinear one. We might be able to achieve a good delta equivalent CDO and CDO2, but the nonlinear effect cannot be matched.

Although theoretically speaking it is the approximation, practically the mapping seems to work well for two reasons. First, because we match the b/e spreads of a CDO trade and a CDO2 trade, the MTM calculated by proxy can be reasonably used for CDO2. Further, as our tests have shown in the next section, the credit spread risk and correlation risk of the RE-CDO and CDO2 agree with each other if the child mezzanine trades have very similar risk profile. The change of the MTM due to the market change of credit spread and implied correlation can be successfully reflected through the proxy CDO.  

Hence as far as capturing daily market change of credit spread and correlation is concerned, the GSP methodology is acceptable if a frequent mapping is performed.

At the present time there is no generally accepted methodology of applying market observed correlation information to a bespoke CDO2 and CDO3 trade. The GSP mapping methodology can be viewed as a roughly delta hedging of a CDO2 or CDO3 trade with a CDO trade. In an ideal case in which each mezzanine tranches has identical risk exposure of correlation and credit shown in this report, it is found that the approximation works very well. 

In general, the approximation will deteriorate when the heterogeneity of the risk exposure of the child mezzanine tranches becomes large and the complexity of the overlapping increases. However, if we only care the small and local movement of the credit spread and correlation and do the mapping frequently, the approximation is acceptable.  For the same reason, the mapping cannot address the scenarios of large and overall shocks such as stress test.

Tests have shown that, given the current market environment, the current choices of weekly mapping and correlation fixed at 0.2 in the mapping are appropriate. However, they should be reviewed frequently. If changing the mapping correlation has a material effect on the implied MTM through proxy CDO, a risk control should be enforced. 


