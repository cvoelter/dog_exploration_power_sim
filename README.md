# Power simulations for the project: Exploration in dogs – motivation, mechanisms, outcomes

| Study | Response variable                       | error structure | test condition         | control condition     | res.sd | N  | power | design  | model                                                                                                     |
| ----- | --------------------------------------- | --------------- | ---------------------- | --------------------- | ------ | -- | ----- | ------- | --------------------------------------------------------------------------------------------------------- |
| 1     | pupil size (baseline corrected)         | gaussian        | incongruent: 500       | congruent: 0          | 350    | 20 | 0.97  | within  | lmer(resp~condition + sex +z.age + z.order + (1+condition|subject))                                       |
| 2     | looking time to setup                   | gaussian        | incongruent: 9         | congruent: 5          | 5      | 68 | 0.89  | between | lm(resp~condition + sex +z.age)                                                                           |
| 2     | first choice of target object           | binomial        | incongruent: 0.67      | congruent: 0.33       |        | 68 | 0.83  | between | glm(resp~condition + sex +z.age, family=binomial)                                                         |
| 3     | number of searched cups in first set    | binomial        | uniform: 3 / 10 lifted | mixed: 7 / 10 lifted  |        | 48 | 0.94  | between | glmer(cbind(lift, not-lifted)~condition + sex +z.age+(1|subject), family=binomial)                        |
| 4     | information seeking (yes / no)          | binomial        | opaque:  0.35          | clear:  0.2           |        | 68 | 0.99  | within  | glmer(resp~condition + sex +z.age+z.block+z.trial+(1+condition+z.block+z.trial|subject), family=binomial) |
|  5/6  | proportion looking time to unseen space | beta            | toy / emotional: 0.4   | no-toy / neutral: 0.2 |        | 32 | 0.94  | between | glm(resp~condition + sex +z.age, family=beta)                                                             |

## Structure 

```
.
├── Study 1           <-- Power analysis of pupil size data using a Linear Mixed Model (LMM).
├── Study 2           <-- Power analysis of looking time and first choice data using a Linear Model (LM) and Generalized Linear Model (GLM; binomial error structure).
├── Study 3           <-- Power analysis of number of searched cups before switch data using a Generalized Linear Mixed Model (GLMM; response matrix as RV, binomial error structure).
├── Study 4           <-- Power analysis of information seeking data using a GLMM (binomial error structure).
├── Study 5/6         <-- Power analysis of proportion looking time data using a GLM (beta error structure).
└── functions         <-- Function for beta GL(M)M. Function kindly provided by Roger Mundry. 

```