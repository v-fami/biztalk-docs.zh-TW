---
title: 單一登入： 事件 10564 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523c97a-608e-4bf4-8747-cfa0cce10acf
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8be4ea87757a1fa0cb5d8ebd2e344ce521dbf740
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997143"
---
# <a name="single-sign-on-event-10564"></a>單一登入： 事件 10564
## <a name="details"></a>詳細資料  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10564                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            不適用                             |
|  符號名稱  |           SSO_ERROR_BACKUP_FILE_INCORRECT_FORMAT           |
|  訊息文字   |     備份檔案並沒有正確的格式。      |
  
## <a name="explanation"></a>說明  
 備份檔案並沒有正確的格式。  
  
## <a name="user-action"></a>使用者動作  
 查看您擁有正確的檔案和位置。 您也應該確認該資料夾中沒有任何其他檔案。BAK 延伸模組，做為 ENTSSO 系統可能會混淆它們實際的備份檔案。