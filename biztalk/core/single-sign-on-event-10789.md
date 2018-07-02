---
title: 單一登入： 事件 10789 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2821694e-e787-4942-8da5-4492e543b4da
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85ad6c7975e78f30872a60462e74ba16b18db0a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997471"
---
# <a name="single-sign-on-event-10789"></a>單一登入： 事件 10789
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                    企業單一登入                                                                     |
| 產品版本 |                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                    |
|    事件識別碼     |                                                                              10789                                                                               |
|  事件來源   |                                                                              ENTSSO                                                                              |
|    元件    |                                                                               不適用                                                                                |
|  符號名稱  |                                                                   ENTSSO_E_DTC_IMPORT_FAILED2                                                                    |
|  訊息文字   | 無法匯入 DTC 交易。 請檢查 MSDTC 已正確設定為支援遠端作業。 請參閱事件記錄檔 （在電腦 '%1'），如需詳細資訊。 |
  
## <a name="explanation"></a>說明  
 無法匯入 DTC 交易。  
  
## <a name="user-action"></a>使用者動作  
 檢查 MSDTC 已正確設定為支援遠端作業，並參閱事件日誌以取得詳細資料指定的電腦上。  
  
 如需 MSDTC 問題的說明，請參閱 < [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。