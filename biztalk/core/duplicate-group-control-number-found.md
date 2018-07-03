---
title: 重複群組控制編號找到 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1badc033-42fd-4992-ad36-b53047ba7817
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66fd37bbfc5be81f7a7301f6313745a29ec180de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001431"
---
# <a name="duplicate-group-control-number-found"></a>找到重複的群組控制編號
## <a name="details"></a>詳細資料  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |                          找到重複的群組控制編號                          |

## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法不處理內送交換因為它有相同的交換、 群組或交易集控制編號和先前已接收的交換。 只要啟用適當的重複控制編號檢查，這會導致失敗。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  

- 請確定 BizTalk Server 傳送的交換並沒有相同的群組控制編號和之前的交換，如果對應的重複控制編號檢查已啟用。  

- 停用重複群組控制編號檢查。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下適當的合作對象，然後開啟 [EDIFACT 交換處理屬性] 或 [X12 交換處理屬性] 對話方塊中，做為交換傳送者合作對象。 若要停用 EDIFACT 交換的檢查，請清除 檢查重複項目 UNG5 （群組控制編號） 交換屬性中。 若要停用檢查的 X12 交換中，清除 檢查重複項目 GS6 （群組控制編號） 交換屬性中。
