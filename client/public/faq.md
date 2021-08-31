# FAQ

## General


### What is PolicyEngine?

PolicyEngine is a tool to democratise tax and benefit analysis. With PolicyEngine, anyone can design a reform to the UK tax and benefit system, and explore the impact of that reform both on the UK overall and on one's individual household.


### Who created PolicyEngine?

PolicyEngine is a product from the [UBI Center](http://ubicenter.org), a research organization studying universal basic income policies. We also developed [OpenFisca-UK](https://github.com/PSLmodels/openfisca-uk), the microsimulation model underlying PolicyEngine. [Nikhil Woodruff](https://www.ubicenter.org/author/nikhil/) is the technical lead and [Max Ghenis](https://www.ubicenter.org/author/max/) is the product manager.


### When will PolicyEngine be available in my country?

Currently, PolicyEngine is only available in the UK, but we're working on bringing it to the US. Want to see PolicyEngine in your country? [Let us know](https://zej8fnylwn9.typeform.com/to/XFFu15Xq)!


### Where can I learn more about how PolicyEngine works?

The code for [PolicyEngine](github.com/ubicenter/policyengine-uk) and for [OpenFisca-UK](https://github.com/PSLmodels/openfisca-uk), the microsimulation model that underlies it, is publicly available on GitHub. We've also answered some common questions below.


### How can I help?

Using and sharing PolicyEngine is already a great help to us! If you'd like to support our work and web hosting fees, please consider [making a donation](https://www.ubicenter.org/donate/). We're also entirely open source, and welcome contributions from developers on [GitHub](github.com/ubicenter/policyengine-uk).


## Policy page


### Do you only simulate policies listed on this page?

No, we simulate essentially the entire tax and benefit system, except for [capital gains tax](https://github.com/PSLmodels/openfisca-uk/issues/40) and [council tax benefit](https://github.com/PSLmodels/openfisca-uk/issues/150). For example, while we don't yet expose parameters on Income Support, we do simulate it for those who are eligible.


### Will you be adding more policy parameters?

Yes, we’re planning to add more tax and benefit parameter options, and other taxes like [land value taxes](https://github.com/UBICenter/policyengine-uk/issues/105) and [carbon taxes](https://github.com/UBICenter/policyengine-uk/issues/104). What would you like to simulate? 


### How can I reset a policy parameter to its current value?

For now, you'll have to change it back using the slider or text box, or reload the page to reset all policy parameters. We're working on a [better way](https://github.com/UBICenter/policyengine-uk/issues/23).


### As of what date are policy parameters set?
We simulate policy as of 2021-01-01, and assume that policy is active throughout 2021. We're working on [updating to the latest policy](https://github.com/UBICenter/policyengine-uk/issues/44).


## UK impact page


### What data do you use to estimate UK-wide impacts?

We use the Family Resources Survey (FRS), the UK's standard survey for estimating poverty. The latest FRS is from 2018-19, and we extrapolate this to 2021 using growth factors published by the ONS and OBR. We also adjust benefit receipt to reflect trends like the Universal Credit rollout.

The FRS underestimates high incomes, so PolicyEngine accordingly will as well; for example, we'll underestimate the revenue from a reform that raises the Additional Rate. We're working on improving the data quality by [adjusting top incomes](https://github.com/PSLmodels/openfisca-uk/issues/103) to better match datasets that accurately capture that population segment.


### What behavioral or macroeconomic assumptions do you make?

None; PolicyEngine is a "static model" only. For example, it assumes that changing marginal tax rates will not affect labour supply.


### How are the reform provisions sequenced for the budgetary impact chart?

Since policy reforms can interact, we do not model them independently. Instead, we start with programs that produce budgetary costs (like new spending programs or tax cuts), ordered from largest to smallest, then do the same with programs that produce budgetary surpluses. This sequence does not follow the order the reforms were specified.


### How is poverty defined?

PolicyEngine reports the change to the absolute poverty rate before housing costs.

_[Learn more about poverty measurement in the UK.](https://osr.statisticsauthority.gov.uk/the-trouble-with-measuring-poverty/)_


### How are the age groups in the poverty chart defined?

Child poverty refers to poverty among people aged 0 to 17. Working age adults are people at least 18 years of age but younger than State Pension age. Retired people are people State Pension age or older.


## Your household page


### How can I remove a household member I've added?

Sorry, but for now you have to reload the page and re-enter your household information. We're working on a [better way](https://github.com/UBICenter/policyengine-uk/issues/101).


### Do you store data about my household?

No, we don't track any household-level information provided by users.


## Household impact page


### What are marginal tax rates and how are they calculated?

Marginal tax rates are the share of an additional pound of income that the state takes, either through reduced benefit payments or through taxes. The baseline tax system has only three marginal rates—the 20% Basic Rate, the 40% Higher Rate, and the 45% Additional Rate—but due to the withdrawal of Universal Credit, the Child Benefit's High Income Tax Charge, the withdrawal of the Personal Allowance, and other features, marginal tax rate schedules are not strictly monotonic. PolicyEngine calculates marginal tax rates with respect to the employment income of the household head ("You" in the _Your household _page).