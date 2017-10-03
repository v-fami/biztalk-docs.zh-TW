---
title: "單一登入： 事件 10561 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 770e6fc1-0854-4555-8f2a-5f199e3aaca7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5148633c7fffabe0ef4bb4789fe4ded58336c10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10561"></a>單一登入： 事件 10561
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10561|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_ERROR_BACKUP_FAILED_MEDIA|  
|訊息文字|指定的主要密碼備份檔案必須位於 NTFS 檔案系統或卸除式 media.%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> 用戶端電腦: %3 %r<br /><br /> 錯誤碼： %4|  
  
## <a name="explanation"></a>說明  
 備份已嘗試使用不正確的媒體，例如 FAT 檔案。 指定用於備份主要密碼必須在 NTFS 檔案系統或卸除式媒體上的檔案。  
  
## <a name="user-action"></a>使用者動作  
 檢查媒體格式，並確定它是 NTFS 或卸除式。