---
title: "SMTP 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b530e39e-c4e7-4b98-be0b-4d02eb2e8dc7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8691da466c2915cee4b8746e20a0d5a96d82d81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-smtp-adapter"></a>SMTP 配接器的已知問題
本節包含可幫助您避免錯誤的資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="error-in-the-biztalk-server-application-log-if-emailbodytextcharset-is-not-defined"></a>如果未定義 EmailBodyTextCharset，會在 BizTalk Server 應用程式記錄檔中產生錯誤  
  
##### <a name="problem"></a>問題  
 如果未定義 EmailBodyTextCharset，會在 BizTalk Server 應用程式記錄檔中產生錯誤，並在 BizTalk Server 應用程式記錄檔中產生類似下列的錯誤：  
  
```  
Event Type:Error  
Event Source:BizTalk Server 2009  
Event Category:BizTalk Server 2009   
Event ID:5754  
Date:9/1/2006  
Time:10:50:11 AM  
User:N/A  
Computer:TEST2006  
Description:  
A message sent to adapter "SMTP" on send port "TIE Test_1.0.0.0_TIE_Test.TieRespTest_Email_Port_4f4f8f4101d5615a" with URI "mailto:approver@BTS2006.com" is suspended.   
Error details: Unknown Error Description   
MessageId: {3F12EBE1-1CDA-44FE-85FE-C2CB8228F287}  
InstanceID: {0616E750-22FF-4380-B413-C94718421340}  
```  
  
##### <a name="cause"></a>原因  
 值必須設定為**EmailBodyTextCharset**參數。  
  
##### <a name="resolution"></a>解決方案  
 指定的值**EmailBodyTextCharset**參數。  
  
## <a name="see-also"></a>另請參閱  
 [SMTP 配接器疑難排解](../core/troubleshooting-the-smtp-adapter.md)