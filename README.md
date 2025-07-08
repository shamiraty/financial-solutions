### MAELEZO YA KIKOKOTOO CHA MKOPO NA FOMULA ZILIZOTUMIKA KWENYE SOFTWARE

#### FEATURES
- Marejesho (Loan Installments)
- Mikopo inayosua-sua marejesho
- Mikopo isiyorejeshwa kabisa
- Mikopo iliyozidishwa marejesho
- Mikopo isiyomaliza marejesho kwa muda uliopangwa
- mikopo iliyofungwa ( imemalizika marejesho)
- Mikopo inayoendelea (ipo ndani ya muda)
- Shedo ya marejesho (Armortization)
- Kupakua data kwa Excel
- Mengine yataongezwa na kubadilishwa kukidhi mahitaji yako

### FOMULA ZILIZOTUMIKA ( UTABADILI NA KUWEKA VALUES  ZAKO )

* **Kiwango cha Riba ya Mwaka (Annual Interest Rate):** 0.25 (25%)
* **Kiwango cha Riba cha Kila Mwezi (Monthly Interest Rate):** 0.25 / 12 
* **Ada ya mkopo (Processing Fee Rate):** 0.0030 (0.30%)
* **Bima (Insurance Rate):** 0.06 (6%)

## Fomula za Kikokotoo cha Mkopo (Loan Calculation Formulas):

* **Malipo ya Kila Mwezi (Monthly Deduction - PMT Formula):**
    `P * r * (1 + r)^n / ((1 + r)^n - 1)`
    Ambapo:
    * `P` = Kiasi Kikuu (Principal - `loan_amount_requested`)
    * `r` = Kiwango cha Riba cha Kila Mwezi (`MONTHLY_INTEREST_RATE`)
    * `n` = Idadi ya Miezi ya Marejesho (`repayment_months`)

    *Ikiwa Monthly Interest Rate ni 0, basi Monthly Deduction = Principal / Months*

* **Jumla ya Mkopo na Riba (Total Loan with Interest):**
    `monthly_deduction * repayment_months`

* **Jumla ya Riba (Total Interest):**
    `total_loan_with_interest - principal`

* **Ada ya Usindikaji (Processing Fee):**
    `principal * PROCESSING_FEE_RATE`

* **Bima (Insurance):**
    `principal * INSURANCE_RATE`

* **Kiasi Kilichotolewa (Disbursement Amount):**
    `principal - (processing_fee + insurance)`

## Ratiba ya Amortization (Amortization Schedule Calculation):

Kwa kila mwezi (`i` kutoka 1 hadi `number_of_months`):

* **Riba Iliyolipwa (Interest Paid):**
    `balance` (salio la mwanzo wa mwezi) `* monthly_interest_rate`

* **Kiasi Kikuu Kilicholipwa (Principal Paid):**
    `monthly_payment - interest_paid`

* **Salio la Mwisho (Ending Balance):**
    `balance` (salio la mwanzo wa mwezi) `- principal_paid`
    *Hakikisha `ending_balance` haishuki chini ya 0.*
