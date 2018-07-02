---
title: 重複少於所需的次數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5bebc13-0e70-4f73-99c0-fed917d79fba
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f0ca660f792494e66d3ad26ead90f8878d80a0d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974887"
---
# <a name="repeats-less-than-required"></a>重複少於所需的次數
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                        X12FeRepeatsLessThanRequiredDescription                         |
|  訊息文字   |                               重複少於所需的次數                               |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示迴圈內外之 X12 交換的區段重複次數少於文件結構描述所要求的次數。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，確定交換中迴圈內外的區段重複結構描述中所指定的次數，然後重新傳送交換。