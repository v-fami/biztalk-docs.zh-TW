---
title: 無效或遺失的 ASN.1 壓縮資料 OID 解壓縮處理過程中發現 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0171daa8-289a-43f1-8cbf-d779ef9dc2ea
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2abc1c0f1331d95ebd331f8f60a947bcca86496
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993575"
---
# <a name="invalid-or-missing-asn1-compressed-data-oid-encountered-during-decompression-processing"></a>無效或遺失的 ASN.1 壓縮資料 OID 解壓縮處理過程中發現
## <a name="details"></a>詳細資料  
  
|                 |                                                                                          |
|-----------------|------------------------------------------------------------------------------------------|
|  產品名稱   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]    |
| 產品版本 |                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                |
|    事件識別碼     |                                            -                                             |
|  事件來源   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI  |
|    元件    |                                        AS2 引擎                                        |
|  符號名稱  |                                            -                                             |
|  訊息文字   | 無效或遺失的 ASN.1 壓縮資料 OID 解壓縮處理過程中發現 |
  
## <a name="explanation"></a>說明  
 此錯誤是指的 ASN.1 壓縮的資料結構。 此錯誤表示寄件者的壓縮資料可以結構壓縮的資料不正確或沒有訊息遭到竄改 （未經授權的變更）。  
  
## <a name="user-action"></a>使用者動作  
 檢閱 壓縮的資料和檢查竄改訊息的結構。