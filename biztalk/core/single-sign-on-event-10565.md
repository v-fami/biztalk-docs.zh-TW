---
title: 單一登入： 事件 10565 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d279491-dc0d-44c4-a77e-a67498a3481d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d31b639853b845169c3360ec6367aee120a266d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007999"
---
# <a name="single-sign-on-event-10565"></a>單一登入： 事件 10565
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                           企業單一登入                                                                                           |
| 產品版本 |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                           |
|    事件識別碼     |                                                                                                     10565                                                                                                     |
|  事件來源   |                                                                                                    ENTSSO                                                                                                     |
|    元件    |                                                                                                      不適用                                                                                                      |
|  符號名稱  |                                                                                       SSO_ERROR_SECRET_VALIDATE_FAILED                                                                                        |
|  訊息文字   | 無法從登錄載入祕密。 SSO 服務的服務帳戶可能已變更，或將密碼可能已損毀。 從備份 file.%r 還原祕密<br /><br /> MSID: %1 |
  
## <a name="explanation"></a>說明  
 很可能到系統中的系統管理員已變更為 SSO 服務帳戶，使無法解密。  
  
## <a name="user-action"></a>使用者動作  
 尋找變更 SSO 服務帳戶的人員，並接著從備份檔案還原祕密。 如需有關還原密碼的詳細資訊，請參閱 <<c0> [ 管理主要密碼](../core/managing-the-master-secret.md)。