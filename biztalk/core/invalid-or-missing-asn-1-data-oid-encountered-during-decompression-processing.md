---
title: "解壓縮處理過程中發現的無效或遺失的 ASN.1 資料 OID |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243062ae-19df-4989-b8d9-109e789f8335
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da26bfb0ff76ec8b78e6572dba14631ff84fd9f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-or-missing-asn1-data-oid-encountered-during-decompression-processing"></a>解壓縮處理過程中發現的無效或遺失的 ASN.1 資料 OID
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|解壓縮處理過程中發現的無效或遺失的 ASN.1 資料 OID|  
  
## <a name="explanation"></a>說明  
 這個錯誤是指 ASN.1 壓縮資料結構。 此錯誤表示壓縮資料寄件者可以是結構壓縮的資料不正確或沒有遭到竄改訊息 （未經授權的變更）。  
  
## <a name="user-action"></a>使用者動作  
 檢閱 壓縮的資料和檢查竄改訊息的結構。