---
title: X12 交易集在 SE01 中有不相符的計數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a90079f5-5939-40b6-9756-d7943240c125
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 947a557a81c6857b5d31f447acb2ec5a46cfcef9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993343"
---
# <a name="the-x12-transaction-set-had-a-mismatched-count-in-se01"></a>X12 交易集在 SE01 中有不相符的計數
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                       |
| 產品版本 |                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                   |
|    事件識別碼     |                                                               -                                                               |
|  事件來源   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                     |
|    元件    |                                                          將 EDI 引擎                                                           |
|  符號名稱  |                                                     X12StSeCountMismatch                                                      |
|  訊息文字   | X12 交易集在 SE01 中有不相符的計數。 SE01 已{0}，但它應該是{1}。 已更正。 |
  
## <a name="explanation"></a>說明  
 這則警告表示交易集結尾 （SE01 欄位） 中的數字，不符合交換的交易集中的區段數目。 傳送管線會更正 SE01 欄位中的計數，並將張貼警告。  
  
## <a name="user-action"></a>使用者動作  
 不需要採取任何動作。