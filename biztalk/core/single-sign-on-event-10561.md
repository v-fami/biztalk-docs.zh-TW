---
title: 單一登入： 事件 10561 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 770e6fc1-0854-4555-8f2a-5f199e3aaca7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053b17fcb940383d58110378710aeb6bc8d3fbe6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992491"
---
# <a name="single-sign-on-event-10561"></a>單一登入： 事件 10561
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                 |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                    企業單一登入                                                                                                    |
| 產品版本 |                                                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                    |
|    事件識別碼     |                                                                                                              10561                                                                                                              |
|  事件來源   |                                                                                                             ENTSSO                                                                                                              |
|    元件    |                                                                                                               不適用                                                                                                               |
|  符號名稱  |                                                                                                  SSO_ERROR_BACKUP_FAILED_MEDIA                                                                                                  |
|  訊息文字   | 所指定的主要祕密備份檔案必須在 NTFS 檔案系統或卸除式 media.%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> 用戶端電腦: %3 %r<br /><br /> 錯誤碼： %4 |
  
## <a name="explanation"></a>說明  
 備份已嘗試使用不正確的媒體，例如 FAT 檔案。 所指定的主要祕密備份檔案必須在 NTFS 檔案系統或卸除式媒體上。  
  
## <a name="user-action"></a>使用者動作  
 檢查媒體格式，並確定它是 NTFS 或卸除式。