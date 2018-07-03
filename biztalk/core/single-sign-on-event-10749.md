---
title: 單一登入： 事件 10749 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10986736-77c0-42a7-b2bb-cd20f9f75fa6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf82eb2fc8312874947af3c035dc13bb8e39a46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010973"
---
# <a name="single-sign-on-event-10749"></a>單一登入： 事件 10749
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                      企業單一登入                                                                                                                      |
| 產品版本 |                                                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                      |
|    事件識別碼     |                                                                                                                                10749                                                                                                                                |
|  事件來源   |                                                                                                                               ENTSSO                                                                                                                                |
|    元件    |                                                                                                                                 N\A                                                                                                                                 |
|  符號名稱  |                                                                                                                       SSO_WARN_PS_CLIENT_PING                                                                                                                       |
|  訊息文字   | 無法連絡目的地 SSO 伺服器。<br /><br /> 請檢查 SSO 服務正在該伺服器上，以及它可以是 contacted.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> SSO 伺服器名稱: %3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 密碼同步處理無法連絡指定的目的地 SSO 伺服器。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 使用 ENTSSO 伺服器嵌入式管理單元來檢查伺服器。  

- 如果未執行，請啟動 「 企業單一登入服務。  

- 請檢查目的地 SSO 伺服器的網路連線。  

- 請檢查目的地 SSO 伺服器上的防火牆。  

  如需詳細資訊，請參閱下列資源：  

- [如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)
