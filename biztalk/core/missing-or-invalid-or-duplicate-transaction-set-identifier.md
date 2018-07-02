---
title: 遺失、 無效或重複的交易集識別項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8580aab2-9fa4-43fb-b643-10621926591e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 476b510396d29d5f4e85a13ed7c3bca3ee3fcef3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971719"
---
# <a name="missing-or-invalid-or-duplicate-transaction-set-identifier"></a>遺失、 無效或重複的交易集識別項
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                      X12TsMissingOrInvalidTsIdentiferDescription2                      |
|  訊息文字   |            遺失、 無效或重複的交易集識別項 '{0}'            |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收或傳送管線無法處理 X12 交換設定值，交易識別碼 （ST01 欄位中），因為已遺失、 重複項目，或具有無效的值。 如果文件結構描述沒有 ST 標頭和 SE 結尾，也可能會發生。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定交換具有 ST01 欄位的值，而且結構描述具有 ST 標頭和 SE 結尾的項目。 確認的 ST01 值是有效的三位數的文件類型指示項。 確認 ST01 欄位不是與另一個交易集合的 ST01 欄位重複。