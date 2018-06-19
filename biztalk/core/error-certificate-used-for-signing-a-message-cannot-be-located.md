---
title: 在本機憑證存放區中找不到用於簽章訊息的憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ff3c7a2-954c-4c62-a7b2-06f7a38d61b3
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94049a0ecca4e7aec89c5163231c0b9bf4c9e3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239958"
---
# <a name="the-certificate-used-for-signing-a-message-cannot-be-located-in-the-local-certificate-store"></a>在本機憑證存放區中找不到用於簽章訊息的憑證
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|CertificateMissingError|  
|訊息文字|在本機憑證存放區中找不到訊息中簽章所用的憑證。 憑證指紋: {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為識別做為簽署憑證的憑證不在必要的憑證存放區中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
1.  藉由開啟 BizTalk Server 管理主控台，以滑鼠右鍵按一下 BizTalk 群組，然後按一下 [憑證] 節點中識別的簽章憑證。  
  
2.  開啟 MMC，嵌入式管理單元新增我的使用者帳戶，然後再開啟憑證，個人和憑證 節點。  
  
3.  請確定目前的使用者憑證存放區包含該簽章憑證的私密金鑰，藉由尋找錯誤訊息文字中識別的憑證指紋。