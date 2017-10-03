---
title: "發出單一函式要求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- single-function requests
- business functions, executing with single-function call
- examples, single-function requests
ms.assetid: 7448c1a7-be88-4ea7-a357-03cd7024729a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a12a91c3f155b3e2e2085edaf15fdbf8f1757f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="issuing-a-single-function-request"></a>發出單一函式要求
下面 GetEffectiveAddress 範例是對 JD Edwards EnterpriseOne 的單一函式呼叫，而這個要求結果會產生標準回應文件。 在單一函式要求中，只會在 XML 物件中指定一個 callMethod。  
  
## <a name="example-executing-a-business-function-with-a-single-function-call"></a>範例： 執行商務功能的單一函式呼叫  
 下面是 GetEffectiveAddress 要求文件範例。 當您加入產生的項目時，BizTalk Server 會從此時所建立的 XSD，依照 XML 執行個體的方式來產生此範例。 這個範例要求文件是使用傳送埠組態中 ATTRIBUTE_STYLE 結構描述樣式所產生的。  
  
 **要求 XML 範例**  
  
```  
<ns0:AddressBookMasterMBF xmlns:ns0=  
"http://schemas.microsoft.com/[JDE://CALLBSFN/N0100041]">   
<ns0:cActionCode>I</ns0:cActionCode>  
<ns0:mnAddressBookNumber>38594</ns0:mnAddressBookNumber>   
  
</ns0:AddressBookMasterMBF>  
  
```  
  
 下列是 J.D.所傳回的 GetEffectiveAddress 回應範例 Edwards EnterpriseOne 針對 GetEffectiveAddress 要求之回覆。  
  
 **回應 XML 範例**  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
  
<N0100041:AddressBookMasterMBFResponse xmlns:N0100041=  
"http://schemas.microsoft.com/[JDE://CALLBSFN/N0100041]">  
<N0100041:cActionCode>I</N0100041:cActionCode>   
<N0100041:cUpdateMasterFile />   
<N0100041:cProcessEdits />   
<N0100041:cSuppressErrorMessages />   
<N0100041:szErrorMessageID />  
<N0100041:szVersion />   
<N0100041:mnSameAsExcept>0</N0100041:mnSameAsExcept>  
<N0100041:mnAddressBookNumber>38594</N0100041:mnAddressBookNumber>   
<N0100041:szLongAddressNumber />   
<N0100041:szTaxId />  
<N0100041:szSearchType>C</N0100041:szSearchType>   
<N0100041:szAlphaName>Jacques Cartier</N0100041:szAlphaName>   
<N0100041:szSecondaryAlphaName>Second Jacques Cartier  
  
</N0100041:szSecondaryAlphaName>   
  
<N0100041:szMailingName>Mailing Jacques Cartier  
</N0100041:szMailingName>   
<N0100041:szSecondaryMailingName>second mailing  
</N0100041:szSecondaryMailingName>   
<N0100041:szDescriptionCompressed>JACQUES CARTIER  
  
</N0100041:szDescriptionCompressed>   
<N0100041:szBusinessUnit>1</N0100041:szBusinessUnit>  
<N0100041:szAddressLine1>Montral</N0100041:szAddressLine1>   
<N0100041:szAddressLine2>3950 Cote Vertu</N0100041:szAddressLine2>   
<N0100041:szAddressLine3>Suite 100</N0100041:szAddressLine3>   
<N0100041:szAddressLine4 />   
<N0100041:szPostalCode>73000</N0100041:szPostalCode>  
<N0100041:szCity>St-Laurent</N0100041:szCity>   
<N0100041:szCounty />  
<N0100041:szState>TX</N0100041:szState>   
<N0100041:szCountry>US</N0100041:szCountry>   
<N0100041:szCarrierRoute />   
<N0100041:szBulkMailingCenter />   
<N0100041:szPrefix1 />   
<N0100041:szPhoneNumber1>514-334-0404</N0100041:szPhoneNumber1>   
<N0100041:szPhoneNumberType1 />   
<N0100041:szPhoneAreaCode2 />  
<N0100041:szPhoneNumber2 />   
<N0100041:szPhoneNumberType2 />   
<N0100041:cPayablesYNM>Y</N0100041:cPayablesYNM>   
<N0100041:cReceivablesYN>N</N0100041:cReceivablesYN>  
<N0100041:cEmployeeYN>N</N0100041:cEmployeeYN>   
<N0100041:cUserCode>N</N0100041:cUserCode>   
<N0100041:cARAPNettingY>N</N0100041:cARAPNettingY>   
<N0100041:cSubledgerInactiveCode />   
<N0100041:cPersonCorporationCode />   
<N0100041:szCertificate />   
<N0100041:szAddlIndTaxID />   
<N0100041:szCreditMessage />  
<N0100041:szLanguage />   
<N0100041:szIndustryClassification />  
<N0100041:cEMail />   
<N0100041:mn1stAddressNumber>38594</N0100041:mn1stAddressNumber>   
  
<N0100041:mn2ndAddressNumber>38594</N0100041:mn2ndAddressNumber>   
<N0100041:mn3rdAddressNumber>38594</N0100041:mn3rdAddressNumber>   
<N0100041:mn4thAddressNumber>38594</N0100041:mn4thAddressNumber>   
<N0100041:mn5thAddressNumber>38594</N0100041:mn5thAddressNumber>   
<N0100041:mnFactorSpecialPayee>38594</N0100041:mnFactorSpecialPayee>   
<N0100041:mnParentNumber>0</N0100041:mnParentNumber>  
<N0100041:cAddressType3YN>N</N0100041:cAddressType3YN>   
<N0100041:cAddressType4YN>N</N0100041:cAddressType4YN>   
<N0100041:cAddressType5YN>N</N0100041:cAddressType5YN>   
<N0100041:szCategoryCode01 />  
<N0100041:szAccountRepresentative />  
<N0100041:szCategoryCode03 />  
<N0100041:szGeographicRegion />   
<N0100041:szCategoryCode05 />  
<N0100041:szCategoryCode06 />  
<N0100041:sz1099Reporting />  
<N0100041:szCategoryCode08 />  
<N0100041:szCategoryCode09 />  
<N0100041:szCategoryCode10 />  
<N0100041:szSalesRegion />   
<N0100041:szCategoryCode12 />  
<N0100041:szLineOfBusiness />  
<N0100041:szSalesVolume />   
<N0100041:szCategoryCode15 />  
<N0100041:szCategoryCode16 />  
<N0100041:szCategoryCode17 />  
<N0100041:szCategoryCode18 />  
<N0100041:szCategoryCode19 />  
<N0100041:szCategoryCode20 />  
<N0100041:szCategoryCode21 />  
<N0100041:szCategoryCode22 />  
<N0100041:szCategoryCode23 />  
<N0100041:szCategoryCode24 />  
<N0100041:szCategoryCode25 />  
<N0100041:szCategoryCode26 />  
<N0100041:szCategoryCode27 />  
<N0100041:szCategoryCode28 />  
<N0100041:szCategoryCode29 />  
  
<N0100041:szCategoryCode30 />  
<N0100041:szGlBankAccount />  
<N0100041:mnTimeScheduledIn>0</N0100041:mnTimeScheduledIn>   
<N0100041:jdDateScheduledIn>2005-06-30</N0100041:jdDateScheduledIn>   
<N0100041:cClearedY />   
<N0100041:szRemark />  
<N0100041:szUserReservedCode />   
<N0100041:jdUserReservedDate>2005-06-30</N0100041:jdUserReservedDate>  
<N0100041:mnUserReservedAmount>0</N0100041:mnUserReservedAmount>   
<N0100041:mnUserReservedNumber>0</N0100041:mnUserReservedNumber>   
<N0100041:szUserReservedReference />  
<N0100041:jdDateEffective>1900-01-01</N0100041:jdDateEffective>   
<N0100041:szProgramId>N0100041</N0100041:szProgramId>   
<N0100041:szRemark1 />   
<N0100041:mnAddNumParentOriginal>0</N0100041:mnAddNumParentOriginal>   
<N0100041:OKToDelete>0</N0100041:OKToDelete>  
<N0100041:szVersionconsolidated />   
<N0100041:cDirectionIndicator />   
<N0100041:cEdiSuccessfullyProcess>0</N0100041:cEdiSuccessfullyProcess>   
<N0100041:szCountryForPayroll />   
<N0100041:szShortcutClientType />   
  
</N0100041:AddressBookMasterMBFResponse>  
```  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 範例檔案](../core/appendix-a-sample-files.md)