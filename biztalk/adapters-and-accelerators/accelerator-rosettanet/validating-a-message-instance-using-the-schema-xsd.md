---
title: "驗證訊息執行個體使用的結構描述 XSD |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema XSD
- validating, messages
- messages, validating
- schemas, XSDs
ms.assetid: c4cbf6b4-130d-4e0f-840b-c8008fafac0b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eda0b76b3daff53290264169c5b2effe80a9e5c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="validating-a-message-instance-using-the-schema-xsd"></a>驗證訊息執行個體使用的結構描述 XSD
本主題描述如何使用 Microsoft?[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 已建置到 RNPIP 組件檔案的其中一個結構描述 XSD 檔案來驗證訊息執行個體。  
  
### <a name="to-validate-a-message-instance-using-the-schema-xsd"></a>若要使用結構描述 XSD 驗證訊息執行個體  
  
1.  啟動**Microsoft Visual Studio 2012**。  
  
2.  在**檔案**，指向 **開啟**，然後按一下 **專案**。  
  
3.  找出*\<磁碟機\>*\Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\schemas 中，按一下**RNPIPs.btproj**，然後按一下 **開啟**。  
  
4.  在 方案總管 中，展開**Rnpip**，以滑鼠右鍵按一下結構描述 XSD，您要用來驗證訊息執行個體，然後按一下 **屬性**。  
  
5.  在 [屬性頁] 對話方塊中，按一下**輸入執行個體檔案名稱**，找出包含檔案的資料夾、 選取訊息執行個體 XML 檔案，然後按一下**開啟**。  
  
6.  按一下 **[確定]**。  
  
7.  在 方案總管 中，以滑鼠右鍵按一下結構描述 XSD，您要用來驗證訊息執行個體，然後按一下 **驗證執行個體**。  
  
## <a name="see-also"></a>請參閱  
 [修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)   
 [使用 PIP](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)