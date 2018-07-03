---
title: 遇到無效的 Adler32 checksum |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa47a208-0f33-496e-8dbe-b50be9979bf2
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acaa60e9d6f1bda4161832cb5ddb34c4e2e9ae93
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987263"
---
# <a name="invalid-adler32-checksum-encountered"></a>無效 Adler32 總和檢查碼時發生
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                     InvalidAdler32ChecksumInCompressedMessageError                     |
|  訊息文字   |                          無效 Adler32 總和檢查碼時發生                          |
  
## <a name="explanation"></a>說明  
 此錯誤是指的 ASN.1 壓縮的資料結構。 此錯誤表示寄件者的壓縮資料可以結構壓縮的資料不正確或沒有訊息遭到竄改 （未經授權的變更）。  
  
## <a name="user-action"></a>使用者動作  
 善用**發現無效的 Adler32 總和檢查碼**表示較高的機率的竄改。 檢查是否有遭到竄改，如果您看到**發現無效的 Adler32 總和檢查碼**。