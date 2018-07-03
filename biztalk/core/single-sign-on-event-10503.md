---
title: 單一登入： 事件 10503 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04292ae8-8daf-4f5a-837e-fe5dfcd02b10
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b90af01551359b5caa1a5404facc9e3fece95673
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990711"
---
# <a name="single-sign-on-event-10503"></a>單一登入： 事件 10503
## <a name="details"></a>詳細資料  

|                 |                                                               |
|-----------------|---------------------------------------------------------------|
|  產品名稱   |                   企業單一登入                   |
| 產品版本 |  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    事件識別碼     |                             10503                             |
|  事件來源   |                            ENTSSO                             |
|    元件    |                              N\A                              |
|  符號名稱  |                SSO_ERROR_SERVICE_START_FAILED                 |
|  訊息文字   | SSO 服務無法啟動。%r<br /><br /> 錯誤碼： %1 |

## <a name="explanation"></a>說明  
 此錯誤事件表示 ENTSSO 服務因為例外狀況所以無法啟動。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [使用 SSO](../core/using-sso.md)
