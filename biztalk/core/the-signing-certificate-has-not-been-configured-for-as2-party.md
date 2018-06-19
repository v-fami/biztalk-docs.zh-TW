---
title: 簽署的憑證尚未針對 AS2 合作對象設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82928a39-3acf-447b-a0e8-f7c25b6f38dc
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61802b5e86319d0fe73f11c22249b72af1441b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279646"
---
# <a name="the-signing-certificate-has-not-been-configured-for-as2-party"></a>簽署的憑證尚未針對 AS2 合作對象設定
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|SigningCertNotConfiguredError|  
|訊息文字|尚未針對 AS2 合作對象設定簽章憑證。  AS2-從： {0} AS2-以： {1}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為未簽署的憑證設定群組。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請透過下列方式設定簽署憑證：  
  
1.  開啟 [BizTalk Server 管理] 主控台。  
  
2.  移至 [群組] 節點，然後按一下 [憑證] 節點。  
  
3.  輸入一般名稱和憑證的指紋。