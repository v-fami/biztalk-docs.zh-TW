---
title: 無法序列化訊息，因為找不到結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37897c04-650d-4695-846d-b8ba61365647
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f366fc619ac070d618345ce6bde9996710b1242
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988183"
---
# <a name="message-cannot-be-serialized-as-the-schema-could-not-be-located"></a>無法序列化訊息，因為找不到結構描述
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                            |
| 產品版本 |                                        [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                        |
|    事件識別碼     |                                                                    -                                                                     |
|  事件來源   |                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                          |
|    元件    |                                                                將 EDI 引擎                                                                |
|  符號名稱  |                                              MessageSerializationFailureDueToMissingSchema                                               |
|  訊息文字   | 訊息不會序列化為結構描述{0}找不到。 結構描述未部署或部署多個複本。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法序列化外, 寄交換因為管線無法判斷它需要用來序列化交換的結構描述。 結構描述可能未部署，或已部署的結構描述的多個複本。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
1.  如果尚未部署與交換關聯的結構描述，開啟 Visual Studio、 結構描述加入 BizTalk 專案，然後建置並部署專案。  
  
2.  如果已部署的結構描述的多個複本，開啟 Visual Studio，並解除部署一份與交換關聯的結構描述。