---
title: 因為驗證失敗處於暫停狀態的批次項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea5e19e8-4592-40f4-bffe-85ab27653fd5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7022041d8d47e1bfa52eb7ef45764c17ed1a2d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279558"
---
# <a name="the-batch-element-is-being-suspended-as-it-failed-validation"></a>批次項目已暫停驗證失敗
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|BatchElementSuspended|  
|訊息文字|驗證失敗的批次項目是已暫停。 錯誤： {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示批次處理協調流程無法將交易設定為批次交換，因為交易設定失敗，批次處理協調流程所執行的驗證。 沒有交易集驗證失敗，就會產生交換。 批次處理協調流程中設定 EDI。BatchElementValidationFailure 內容屬性為"True"。 BatchSuspend 協調流程將會根據該內容屬性收取訊息、發佈錯誤資訊，然後再擱置訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，表示寄件者的交易集發生的錯誤，錯誤訊息中所示。 已解決的問題，導致無法通過驗證，然後再重新傳送交易集合寄件者。