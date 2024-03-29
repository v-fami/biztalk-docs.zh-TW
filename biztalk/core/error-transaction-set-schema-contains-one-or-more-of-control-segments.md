---
title: 交易集結構描述包含一或多個控制區段 ISA、 IEA、 GS、 GE |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7589d8f0-c727-47df-afbc-77b0f190f3e2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f0ab50802cbb872d7ba884a8256824426fbe098
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008201"
---
# <a name="transaction-set-schema-contains-one-or-more-of-control-segments-isa-iea-gs-ge"></a>交易集結構描述包含一或多個控制區段 ISA、 IEA、 GS、 GE
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                       SchemaCode114EOtherControlSegmentsPresent                        |
|  訊息文字   |    交易集結構描述包含一或多個控制區段 ISA、 IEA、 GS、 GE    |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交易集，或傳送管線無法處理外寄交易集因為交易集的文件結構描述定義至少一個ISA、 IEA、 GS 或 GE 區段。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，解除部署文件結構描述、 ISA、 IEA、 GS 或 GE 區段移除結構描述，然後重新部署結構描述。