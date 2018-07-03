---
title: 單一登入： 事件 10706 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9e56600b86856af6a9cdb14fd2a902b047e84b5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022452"
---
# <a name="single-sign-on-event-10706"></a>單一登入： 事件 10706
## <a name="details"></a>詳細資料  

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                 企業單一登入                                                 |
| 產品版本 |                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                 |
|    事件識別碼     |                                                           10706                                                           |
|  事件來源   |                                                          ENTSSO                                                           |
|    元件    |                                                            N\A                                                            |
|  符號名稱  |                                                SSO_WARN_PS_NO_GLOBAL_SYNC                                                 |
|  訊息文字   | 群組配接器需要全域旗標允許密碼同步處理。 檢查全域旗標。%r<br /><br /> 配接器： %1 |

## <a name="explanation"></a>說明  
 這個警告事件表示外部密碼同步配接器已要求密碼同步，且兩者皆非全域的旗標的設定。 有兩個旗標，可讓傳送密碼至外部系統的其中一個： SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL，另一個可接收外部系統 SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB 的密碼。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

-   使用 SSO 管理 MMC 嵌入式管理單元，(系統&#124;屬性&#124;選項) 或命令列工具`ssomanage –enable winsync/extsync`若要啟用全域旗標。  

## <a name="more-info"></a>其他資訊

- **企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)
