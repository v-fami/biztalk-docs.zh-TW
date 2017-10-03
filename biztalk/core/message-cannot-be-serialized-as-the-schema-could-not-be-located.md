---
title: "無法序列化訊息，因為找不到結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37897c04-650d-4695-846d-b8ba61365647
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b887d4a07d7a461278d3858289882a9ce441e9e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-cannot-be-serialized-as-the-schema-could-not-be-located"></a>無法序列化訊息，因為找不到結構描述
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|MessageSerializationFailureDueToMissingSchema|  
|訊息文字|無法序列化訊息，因為找不到結構描述 {0}。 無法部署結構描述或部署多個複本。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法序列化到外寄交換因為管線無法判斷它需要用來序列化交換的結構描述。 結構描述可能未部署或部署的結構描述的多個複本。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
1.  與交換關聯的結構描述尚未部署，如果開啟 Visual Studio、 結構描述加入 BizTalk 專案，然後建置並部署專案。  
  
2.  如果已部署的結構描述的多個複本，開啟 Visual Studio，並解除部署，但其中一個結構描述與交換關聯的複本。