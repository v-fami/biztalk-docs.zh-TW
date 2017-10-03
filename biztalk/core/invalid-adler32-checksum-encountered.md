---
title: "無效 Adler32 總和檢查碼遇到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa47a208-0f33-496e-8dbe-b50be9979bf2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c069e6435c3840e9a535d492943dfc3956a513f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-adler32-checksum-encountered"></a>無效 Adler32 總和檢查碼遇到
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|InvalidAdler32ChecksumInCompressedMessageError|  
|訊息文字|無效 Adler32 總和檢查碼遇到|  
  
## <a name="explanation"></a>說明  
 這個錯誤是指 ASN.1 壓縮資料結構。 此錯誤表示壓縮資料寄件者可以是結構壓縮的資料不正確或沒有遭到竄改訊息 （未經授權的變更）。  
  
## <a name="user-action"></a>使用者動作  
 使用**遇到無效的 Adler32 總和檢查碼**表示機率很高的資料遭到竄改。 檢查是否有遭到竄改，如果您看到**遇到無效的 Adler32 總和檢查碼**。