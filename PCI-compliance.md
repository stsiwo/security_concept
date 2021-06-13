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
 
