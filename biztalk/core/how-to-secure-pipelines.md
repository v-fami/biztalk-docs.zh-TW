---
title: "如何保護管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3a717f-acf8-4f08-a6fb-6d1d48b5b80a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 903e9faec81ce58aac243fb7a22bac6678a81a42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-secure-pipelines"></a>如何保護管線

## <a name="authentication-trusted"></a>信任的驗證
主機可以在管理主控台中標示**信任的驗證**。 將主控件標示為 [信任的驗證] 表示 Microsoft BizTalk Server 將會信任該主控件所傳送訊息內容的安全性相關屬性。 在訊息內容 的安全性相關屬性**OriginatorPID**，對應於訊息內容屬性 BTS。SourcePartyID，而**OriginatorSID**，對應於訊息內容屬性**BTS。WindowsUser**。 如需詳細資訊，請參閱**訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
 主控件標示為**驗證信任**允許指定的受信任的主機新增訊息至佇列本身以外的任何人為訊息的寄件者。 換句話說，主機未標示為**信任的驗證**不允許將訊息加入佇列，他自己以外的訊息寄件者。  
  
> [!IMPORTANT]
>  MIME/SMIME 解碼器管線元件不會檢查解密憑證的到期日。 然而，它會檢查簽章憑證的到期日。  
  
 編碼和解碼訊息透過 SMTP 或 HTTP 的相關資訊，請參閱[MIME SMIME 編碼器管線元件](../core/mime-smime-encoder-pipeline-component.md)。 另請參閱[MIME SMIME 解碼器管線元件](../core/mime-smime-decoder-pipeline-component.md)。  
  
 如需處理協力廠商時的簽章驗證資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。 另請參閱[如何建立協議](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c)。  
  
## <a name="see-also"></a>另請參閱  
 [建立管線使用管線設計師](../core/creating-pipelines-using-pipeline-designer.md)   
 [開發自訂管線元件](../core/developing-custom-pipeline-components.md)