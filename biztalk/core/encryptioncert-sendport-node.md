---
title: EncryptionCert （SendPort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EncryptionCert node [binding file]
ms.assetid: 83dff67e-1b3c-4c3d-91a2-d826a498635f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd51f4b339c5bdd228c692fffd7e6c487bb8c0ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="encryptioncert-sendport-node"></a>EncryptionCert (SendPort 節點)
繫結檔案的 SendPort 節點的 EncryptionCert 節點中，包含搭配隨同繫結檔案匯出之傳送埠所使用的加密憑證的相關資訊。  
  
## <a name="nodes-in-the-encryptioncert-node"></a>EncryptionCert 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|LongName|Attribute|xs:string|指定憑證的完整名稱。|不需要|預設值：空白|  
|ShortName|Attribute|xs:string|指定憑證的簡短名稱。|不需要|預設值：空白|  
|UsageType|Attribute|CertUsageType (SimpleType)|指定這個憑證的預定使用方式|Required|預設值：無<br /><br /> 可能的值包括用於[Microsoft.BizTalk.ExplorerOM.CertUsageType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.certusagetype.aspx)列舉型別。|  
|ThumbPrint|Attribute|xs:string|指定憑證的指紋 (或唯一識別碼)|不需要|預設值：空白|