---
title: SMTP 配接器組態屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SMTP adapters, properties
- SMTP adapters, code sample
- SMTP adapters, send ports
- send ports, adapters
ms.assetid: 6af287f5-272a-42d7-9878-99a4157c06ce
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8b8bb0c5562c07260a9d411b8144bd7a576eb3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279398"
---
# <a name="smtp-adapter-configuration-properties"></a>SMTP 配接器組態屬性
下表列出可為 SMTP 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|DeliveryReceipt|VT_BOOL|指定傳遞訊息之後應傳送確認電子郵件訊息。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|來源|VT_BSTR|指定要置於 SMTP 之「寄件者」標頭的電子郵件地址。|最小長度：00<br /><br /> 最大長度：256|無|  
|MessagePartsAttachments|VT_UI4|指定如何將 BizTalk 訊息部分附加到電子郵件訊息。|有效值為：<br /><br /> -0 （不要附加訊息部分）<br />-1 （附加唯一內文部分<br />-2 （附加所有部分）|預設值為 0 (不要附加訊息部分)。|  
|副本|VT_BSTR|指定傳送訊息副本的電子郵件地址。|最大長度： 1024年|您可以指定多個地址。|  
|SMTPAuthenticate|VT_UI4|有效值為：<br /><br /> -0 （不驗證）<br />-1 （基本驗證）<br />-2 （處理序帳戶 (NTLM)）|若未指定此值，則會套用 (預設) 值。|(預設) 值表示 SMTP 傳送埠將會使用在傳送處理常式中指定的組態值。|  
|使用者名稱|VT_BSTR|指定要用於 SMTP 伺服器驗證的使用者名稱。|除非 SMTPAuthenticate 屬性設定為 [1 (基本驗證)]，否則此屬性不需要值。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|無|  
|EmailBodyFileCharset|VT_BSTR|指定正在傳送之檔案的字元集編碼。|除非已設定 EmailBodyFile 屬性，否則此屬性不需要值。|SMTP 配接器不會將指定的編碼套用至檔案，這個選項只用於指定所傳送檔案的編碼方式。<br /><br /> 預設值為 utf-8。|  
|EmailBodyText|VT_BSTR|指定傳送的電子郵件內文所使用的文字。|最大長度：64KB|無|  
|ReadReceipt|VT_BOOL|指定讀取訊息之後應傳送確認電子郵件訊息。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|若要|VT_BSTR|指定傳送訊息目標的電子郵件地址。|無|無|  
|EmailBodyFile|VT_BSTR|指定檔案的路徑，此檔案將用於傳送的電子郵件內文。|路徑最大長度：256 個字元|建議的最佳作法是指定一個檔案共用上的路徑，該檔案共用可從用於執行執行的 BizTalk Server 群組中的所有 BizTalk Server 存取。|  
|主旨|VT_BSTR|指定訊息的主旨標題。|最小長度：00<br /><br /> 最大長度：256|無|  
|密碼|VT_NULL|指定要用於 SMTP 伺服器驗證的密碼。|這個屬性不需要值，除非 SMTPAuthenticate 屬性設定為 1 （基本驗證）。<br /><br /> 當匯出繫結檔案時，一定會將這個值設定為 Null。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。|無|  
|附加檔案|VT_BSTR|指定檔案的路徑，此檔案將附加至傳送的電子郵件。|路徑最大長度：256 個字元|無|  
|SMTPHost|VT_BSTR|指定傳送訊息時要使用的 SMTP 伺服器名稱。|傳送埠或接收位置的 URI 不能超過 256 個字元。<br /><br /> 路徑最大長度：256 個字元|無|  
|EmailBodyTextCharset|VT_BSTR|指定用以編碼傳送之電子郵件內文的字元集。|除非已設定 EmailBodyText 屬性，否則此屬性不需要值。|預設值為 utf-8。|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
<DeliveryReceipt vt="11">-1</DeliveryReceipt>  
<From vt="8">someone@microsoft.com</From>  
<MessagePartsAttachments vt="19">0</MessagePartsAttachments>  
<CC vt="8">someoneelse@microsoft.com</CC>  
<SMTPAuthenticate vt="19">1</SMTPAuthenticate>  
<Username vt="8">OverrideUsername</Username>  
<EmailBodyFileCharset vt="8">utf-8</EmailBodyFileCharset>  
<EmailBodyText vt="8">Email Body Text</EmailBodyText>  
<ReadReceipt vt="11">-1</ReadReceipt>  
<To vt="8">recipient@microsoft.com</To>  
<EmailBodyFile vt="8">C:\emailbodyfile.xml</EmailBodyFile>  
<Subject vt="8">test mail</Subject>  
<Password vt="1" />  
<Attachments vt="8">C:\attachment.txt</Attachments>  
<SMTPHost vt="8">emailhost</SMTPHost>  
<EmailBodyTextCharset vt="8">utf-8</EmailBodyTextCharset>  
</CustomProps>  
```