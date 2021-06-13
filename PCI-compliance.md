# PCI compliance 

## purpose 

  - to protect payment (credit-card) info from sealing on the web

## terms

  - credit card:
    - sensitive cardholder data:
      - CID: 3 or more digit of backside of credit card 
      - PAN: primary payment number
      - Chip:
      - Cardholder Name: 
      
  - primary account number (PAN or payment card numbers)
    - up to 19-digit number generated as a unique id for a primary account.
    - it appears on the front of your credit/debit card
    
  - cardholder data environment (CDE):
    - def) the people, processes and technologies that store, process, or transmit credit card data - or any system connected to it.
    
  - Payment Card Industry Security Data Security Standards (PCI DSS) 
    - def) a standard to ensure a baseline level of protection for consumers and banks in the Internet era.
    - it has over 1,800 pages of official documentation and you may be required to meet each of the 300+ security controls. => so tough!!
      
  - Card-not-present transaction: a payment card transaction made where the cardholder does not or cannot physically present the card for a merchant's visual examination at the time that an order is given and payment effected. 
      
  - MOTO transaction (Mail Order/Telephone Order)
      
## When to need follow this compliance

  - if the sensitive credit card goes to your own server, even if it is a very short time, requires 300+ security controls in PCI DSS.
  
  - if the compnay does not need to handle sensitive credit card data, such as outsourcing payment system (like Stripe), you just need to confirm 22 security controls, most of which are straightforward, such as using strong passwords. 
  
  * KEY: whether credit card info is transmitted to your server even if very short time.
    - if so, you need to follow the compliance heavily 300+ security controls
    - if not, you just need 22 security controls.
    
## If you store credit card info in your database:
  - you need to define CDE to properly segment the payment environment from the rest of the business so as to limit the scope of PCI validation.
  - if you don't do that, the PCI security controls apply to every syste, laptop, and device on its corporate network. worst case!!!
      
## where the sensitive cardholder dat can be stolen?
  - compromised card reader
  - paper stored in a filing cabinet
  - database
  - hidden camera recofing entry of authentication data
  - man-in-midddle
  
## what neeeds to be secure?
  - network routers
  - database
  - transmission
  - online payment applications and shopping carts
  
## PCI  3-step process
  - it is not one-time compliance. this thought causes false sense of security
  - rather, it should be long-time process.
  
  step1: access. identify vulnerabilities
  step2: remediate: fix the vulnerabilities
  step3: report
  
## the way to achieve compliance procedures is depends on the card brands

## implementation PCI data security standard
  - 1. scoping: identifying all system components that are involves cardholder data environment (people, processes, and technology)
  
  - 2. assessment: 
    - qualified security assessor: a data security firm to perform on-site PCI data security standard assessments
    - approved scanning vendor: a data security firm that uses a scanning solution to determine
      whether or not the customer meets the external vulnerability scanning requirement.
        - perform external network and system scans
        - for external system
        
    3. report
      - report assessment result (compliance status) to financial institution/credit card brands

## Annual validation:
  - any company who deals with credit card need to complete a PCI validation form annally. 
  
## Requirements (PCI DSS v3.2.1)
  - LEVEL: 1 - 4
    - based on the number of transactions or breach experience or card association request.
    
  - SAQ varies based on the level.

## Self-Assessment Questionnaire (SAQ)
  - it is designed as a self-validation tool to access security for cardholder data for *small* merchants and service providers
  - yes or no questions
  - if no, may required to state the future remediation date and associated actions
  - there are different SAQ based on the different merchant environment
      
  - steps
    - check document: https://www.pcisecuritystandards.org/document_library?category=saq&document=saq
    - 1. make sure your environment is met its SAQ type (e.g., A, A-EP)
    - 2. make sure the scope (Attestation of Compliance)
    - 3. assesss (complete) questionnaire in the document
    - 4. submit SAQ nad Attestation of Compliance to credit card brands or financial 
    
  - types:
    - A: (Card-not-present merchants*) full outsource. no electronic storage, processing, or transmission of any cardholder data on the merchant's systes or premises.
    
    - A-EP: (E-commerce merchants): outsource all payment processing to PCI DSS validated third parties and who have a website(s) that does n't directly receive cardholder data but that can impact the security of the payment transaction. 
     
     diff: https://epayments-support.ingenico.com/en/direct/faq/comparison-of-the-saq-a-vs-saq-a-ep
    
    - ...
    
### 4 requirements (SAQ A) : June 11th, 2020.

  2. Do not use vendor-supplied defaults for system passwords and other security parameters:
    - don't use default password/setting for my system (e.g., os, software, and anything what involving the payment system)
    - remove unnecessary default accounts

  6. Develop and maintain secure systems and applications:
    - the all system components are protected by known vulnerabilities by security patches installed.
    - critial security patches is up to date. (within one month)

  8. Identify and authenticate access to system components:
    - must have a unique id for each user who access to your system/cardholder data
    - password is set to all user who access to the system
    - immediate deactivation/removal account if the user terminate its account
    - password must follow:
      - min 7 chars length, and
      - contains numeric and alphabetic chars
      - or has complexity equivalent to above 
    - no generic user IDs and accounts (e.g., login as Admin, Student, or Clerk)
      - should login as Name/Password
    - no shared user IDS for sysem admin (shared user id: an id used for multiple users)

  9. Restrict physical access to cardholder data
    - all media (e.g., computers, papers, reports, faxes, and electronic media) is secured.
      - remove every hardcopies if no longer needed.
      - ...
  12. Maintain a policy that addresses information security for all personnel
    - personnel: full-time, part-time employees, temporary employees who are involved in this system.
  

  SAQ A official form: https://www.pcisecuritystandards.org/documents/PCI-DSS-v3_2_1-SAQ-A.pdf?agreement=true&time=1623568416737
  
    
## Integration with Stripe:

   - the integration with Stripe, is certified as a PCI level 1 Service Provider, allows us to reduce the burden of CPI requirement.
   
   - the simplest way for you to be PCI compliant is to never see (or have access to) card data at all so that you can protect customer credit card and Stripe can does PCI compliance and make you simplify the PCI task.
   
   - follow this:
    
        1. use one of 'payments integrations' to collect payment information, which is securely transmitted directly to Stripe without it passing through your servers
        
        2. serve your payment pages securely using TLS so that they make use of HTTPS Review and validate your account's PCI compliance annually. 
        
   - all Stripe users must validate their PCI compliance annually. 
    - you need to do SAQ.
      - type of SAQ depends on how you integrated Stripe and which of the methods (see below) you use to collect card data. 
      
        method list)
          - Checkout/Elements => Pre-filled SAQ A 
            - Stripe automatically creates a combined SAQ A and Attestation of Compliance (AoC) for you. 
            - no action is required on your part to submit further proof of your PCI compliance. 
               => what does it means? don't need to submit SAQ? or don't need to touch anything but you need to submit SAQ? if so to where?
          - Terminal
          - Mobile SDK 
          - Stripe.js v2
          - Dashboard
          - API Direct
          - Connect
      
      
      - Stripe determines what documentation for SAQ might be required based on how you're processing payments and provides this information in 
    
      - the response from Stripe, which is non-sensitive card information such as the cart type, the last four digits of the card, and expiration date. THIS INFORMATION IS NOT SUBJECT TO PCI COMPLIANCE, 

### Flow with Stripe (Simplest & Easy)

  1. serve your website via HTTPS.
  2. use Stripe Checkout/Elements.
    - this makes your website out of scope of PCI compliance since your server never touch any sensitive information. 
    - so you just need to do SAQ (type: A)
  3. you will receive the completed SAQ
  4. review the SAQ (don't need to submit SAQ if your business is small. see the criteria)

  ref: https://stackoverflow.com/questions/22029611/do-need-to-worry-about-pci-compliance-if-i-use-stripe-or-authorize-net-with-wooc

# Q&A

## DSS 3.2 has strict password policy, but Google, Facebook, and others don't follow the policy. why?

  - password policy: 
    - Users to change passwords at least every 90 days.
    - ...
  
  - many companies don't implement this. why?
    - important point is that the account can access to cardholder data or not.
    - if the account can access to it, you need to follow the strict password policy.
    - if not, you don't need to.

  - quote from DSS 3.2
  ```
    Note: These requirements are applicable for all accounts, including point-of-sale accounts, with administrative capabilities and all accounts used to view or access cardholder data or to access systems with cardholder data. This includes accounts used by vendors and other third parties (for example, for support or maintenance). These requirements do not apply to accounts used by consumers (e.g., cardholders). 
  ```
  - ref: https://security.stackexchange.com/questions/151381/to-whom-do-the-pci-dss-password-requirements-apply
