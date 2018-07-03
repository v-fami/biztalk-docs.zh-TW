---
title: 解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7caf047-badd-49e8-b955-554e5ec7511f
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1ee1388304eb9923dcd2c6fef1468794f7c622a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012847"
---
# <a name="invalid-asn1-zlib-compression-field-encountered-during-decompression-processing"></a>解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                          InvalidOptionalZLibFieldEncountered                           |
|  訊息文字   |    解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位    |
  
## <a name="explanation"></a>說明  
 此錯誤是指的 ASN.1 壓縮的資料結構。 此錯誤表示寄件者的壓縮資料可以結構壓縮的資料不正確或沒有訊息遭到竄改 （未經授權的變更）。  
  
## <a name="user-action"></a>使用者動作  
 檢閱 壓縮的資料，並檢查被竄改的辨識項的結構。