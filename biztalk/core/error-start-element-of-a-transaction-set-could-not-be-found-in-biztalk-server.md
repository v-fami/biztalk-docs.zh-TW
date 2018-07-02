---
title: 處理交易集因為找不到交易集的開始項目後所發生的錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5380aee-1632-4cdf-98a1-aff87574ce4f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74ea9b059ed75d88a8f48287d553e670d2c7d755
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984479"
---
# <a name="error-encountered-after-processing-transaction-sets-because-the-start-element-of-a-transaction-set-could-not-be-found"></a>處理交易集因為找不到交易集的開始項目後所發生的錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| 產品版本 |                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    事件識別碼     |                                                         -                                                         |
|  事件來源   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI               |
|    元件    |                                                    將 EDI 引擎                                                     |
|  符號名稱  |                                             InvalidEfactBiboXmlFormat                                             |
|  訊息文字   | 在處理之後所發生的錯誤{0}交易集。 找不到交易集的開始項目。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交易集，因為接收管線找不到 ST 或 UNH 標頭。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請連絡寄件者的交換，並讓它們確定的交易集錯誤開頭的 ST01 或 UNH1 的區段。