---
title: "批次處理協調流程中的批次提交期間發生持續性例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf6e832f-9d01-46e7-aaf5-2b402d509fac
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eae4f48209dc4f5afefbc69c40706a31f2b00b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="a-persistence-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a>批次處理協調流程中的批次提交期間發生持續性例外狀況
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|PersistenceExceptionOccured|  
|訊息文字|在批次處理協調流程中的批次提交期間發生持續性例外狀況。 批次識別碼 = {0}，ErrorMessage = {1}。 請檢查您的傳送埠訂閱，並加以修正。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，BizTalk Server 無法傳送的批次的交換因為任何傳送埠不訂閱該交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定傳送埠訂閱批次所設定的傳送埠的下列篩選屬性： EDI。DestinationPartyName = \<PartyName >，EDI。BatchEncodingType = EDIFACT 或 X12，以及 EDI。ToBeBatched = False。