---
layout: default
title: Optimized Institutional Staking Strategy
---

##### **Document Version:** 1.3
##### **Date:** Febuary 9, 2024
##### **Author:** Benjamin Zawodni - Founder CEO - [Hodler Staking Services](https://www.hodlerstaking.com/)

---

## **1. Executive Summary**

This document outlines an optimized staking strategy for institutional investors operating private Cardano stake pools. The strategy centers on maximizing rewards by converting the maximum practical amount of delegated ADA to pledged ADA, leveraging the Cardano reward mechanism's incentive structure for higher pledge.  This approach, applied to fully self-funded, private pools, results in a quantifiable increase in Return on Investment (ROI) compared to strategies with lower pledge ratios.  The analysis includes a mathematical derivation of the reward formula and a clear demonstration of the percentage increase in rewards achievable through full pledge.

## **2. Introduction**

Cardano's Ouroboros Praos consensus mechanism distributes staking rewards to incentivize participation and secure the network. Stake pool operators (SPOs) can influence their rewards through operational parameters, most notably the pledged amount of ADA. This document focuses on a specific scenario: an institutional investor operating a *private*, *self-funded* stake pool, meaning the investor controls 100% of the stake.  In this context, "optimized" refers to maximizing the total ADA rewards received by the investor, acting as both pool operator and sole delegator.

## **3. Cardano Reward Mechanism Overview**

The Cardano reward formula, central to this strategy, is defined as follows:


![Formula image]({{ "/assets/pledge_formula.png" | relative_url }}){: width="400px"}


**Where:**

*   **`R`:** Total ADA rewards available for distribution in a given epoch.
*   **`a0`:** Pledge influence parameter (a protocol-defined constant). A higher `a0` increases the impact of pledge on rewards.
*   **`z0`:** Saturation parameter (defined as `1/k`, where `k` is the desired number of pools – a protocol parameter). Represents the saturation point, or the optimal pool size.
*   **`σ`:** Relative stake of the pool (Total Pool Stake / Total Circulating ADA Supply).
*   **`s`:** Relative pledge (Pledged ADA / Total Circulating ADA Supply).
*   **`σ' = min(σ, z0)`:** The relative stake of the pool, capped at the saturation point.
*   **`s' = min(s, z0)`:** The relative pledge, capped at the saturation point.

**Reward Distribution:**

1.  **Pool Rewards Calculation:** The total rewards a pool is eligible for are calculated using the formula above.
2.  **Operator Cost Deduction:** The pool operator's fixed cost (`β`) is deducted from the total pool rewards.
3.  **Operator Margin Deduction:**  A percentage (`α`, the pool margin) of the remaining rewards is taken by the operator.
4.  **Proportional Distribution:** The remaining rewards are distributed proportionally among all delegators, *including the pool operator based on their pledged stake*.  In a private pool, the operator receives *all* of this remaining portion. Therefore, the operator's total rewards simplifies to the pool rewards: `Operator Rewards = Rewards`.

## **4. Optimized Strategy: Full Pledge**

For a private, self-funded pool, the optimal strategy to maximize total rewards is to convert all delegated ADA to pledged ADA. This means setting `s = σ`.  We will analyze a scenario where the pool is operating below saturation, at 93% saturation.

#### **4.1 Scenario: 93% Saturated Pool**

Let's assume the pool holds 93% of the saturation level (`z0`).  Therefore:

*    `σ_initial = 0.93 * z0 = 0.93 / k`
*    Initial pledge `s_initial= 0`
*    Final pledge `s_final = σ_initial`

#### **4.2 Mathematical Derivation of Reward Increase**
Initial Rewards (Before Pledge Increase):

With zero initial pledge (`s_initial = 0`), the initial pool rewards are:
```
Rewards_initial = R * (σ_initial) / (1 + a0)
= R * (0.93 / k) / (1 + a0)
```
**Final Rewards (After Full Pledge):**

After converting all delegation to pledge, `s_final = σ_initial = 0.93 / k`. The pool rewards become:
```
Rewards_final = R * (σ_initial + (s_final * a0 * ((σ_initial - s_final * ((z0 - σ_initial) / z0)) / z0)))/ (1 + a0)
= R * (0.93/k) * (1 + a0 * 0.93^2) / (1 + a0)
```
**Percentage Increase in Rewards:**
The percentage increase in rewards is the key metric:
```
Percentage Increase = ((Rewards_final - Rewards_initial) / Rewards_initial) * 100
=  ((R * (0.93/k) * (1 + a0 * 0.93^2) / (1 + a0) - R * (0.93 / k) / (1 + a0)) / (R * (0.93 / k) / (1 + a0))) * 100
= (a0 * 0.93^2) * 100
```

**Key Result:** 
**The percentage increase in rewards simplifies to `(a0 * 0.93^2) * 100`.  This is *independent* of the total rewards (`R`), the pool's total stake, and the saturation parameter (`z0`).**

#### **4.3 Numerical Example**

**For example, with `a0 = 0.3`:**

```
Percentage Increase = 0.3 * 0.93^2 * 100 = 25.947%
```
#### Therefore, converting all delegated ADA to pledge in this 93% saturated, private pool scenario increases total rewards by approximately:
### **25.95%**.
---

## **5. Benefits of Full Pledge**

*   **Maximized Rewards:** As demonstrated mathematically, full pledge significantly increases the total ADA rewards earned by the pool operator in a private pool scenario.
*   **Simplified Operations:**  Managing a single pledged wallet simplifies stake key management and reward tracking compared to managing separate pledge and delegation wallets.
*   **Full Control:** The operator retains complete control over their stake and is not reliant on external delegators.

## **6. Risks and Mitigation**

*   **Liquidity:** Pledged ADA is not 'locked' and can be transfered at any time. It does have some reduced liquidity compared to delegated ADA due to the un-pledging process, which if bypassed, could result in a temporary reduction in staking returns from the pool.
    *   **Mitigation:** Maintain a separate wallet with a amount of liquid ADA for operational needs and potential emergencies.
*   **(Theoretical) Protocol Changes:** Future Cardano protocol updates could *theoretically* alter the reward mechanism, although significant changes impacting this strategy are unlikely.
    *   **Mitigation:** Stay informed about Cardano Improvement Proposals (CIPs) and protocol updates.

## **7. Conclusion**

**For institutional investors operating private, self-funded Cardano stake pools, converting all delegated ADA to pledged ADA represents an optimized staking strategy. This approach leverages the Cardano reward mechanism to achieve a substantial and quantifiable increase in total rewards.  The mathematical derivation and numerical example clearly demonstrate the benefits, with a potential ROI increase of approximately 25.95% (assuming `a0 = 0.3`) for a 93% saturated pool.  While minor risks exist, they are easily mitigated through careful planning and liquidity management. This strategy provides a clear path to maximizing returns on Cardano staking investments for institutional participants.**

## **8. Refrences**
* Protocol Documentation: [https://docs.cardano.org/about-cardano/learn/pledging-rewards](https://docs.cardano.org/about-cardano/learn/pledging-rewards)
* Cardano Improvement Proposals: [https://cips.cardano.org/](https://cips.cardano.org/)