---
title: 單一登入： 事件 10759 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5347f3d6-d31a-4c00-a64c-c0b0f680de88
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 177b5d1383a583ddc33a67a7290bff98b1d13364
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967583"
---
# <a name="single-sign-on-event-10759"></a>單一登入： 事件 10759
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                             企業單一登入                                             |
| 產品版本 |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    事件識別碼     |                                                       10759                                                       |
|  事件來源   |                                                      ENTSSO                                                       |
|    元件    |                                                        不適用                                                        |
|  符號名稱  |                                       ENTSSO_E_BACKUP_RESTORE_FAILED_MEDIA                                        |
|  訊息文字   | 針對主要密碼備份或還原指定的檔案必須位於 NTFS 檔案系統或卸除式媒體。 |
  
## <a name="explanation"></a>說明  
 只有 NTFS 檔案系統或卸除式媒體可以進行保護。  
  
## <a name="user-action"></a>使用者動作  
 切換至 NTFS 檔案系統來備份主要密碼的卸除式媒體。