---
title: 單一登入： 事件 10708 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63675191-41cb-43fc-9355-e4ddc3f354c5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b052e3545aa67b27bc94de579faedde782c0dec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003087"
---
# <a name="single-sign-on-event-10708"></a>單一登入： 事件 10708
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                   企業單一登入                                                    |
| 產品版本 |                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                   |
|    事件識別碼     |                                                             10708                                                              |
|  事件來源   |                                                             ENTSSO                                                             |
|    元件    |                                                              N\A                                                               |
|  符號名稱  |                                                    SSO_WARN_PS_NO_WIN_SYNC                                                     |
|  訊息文字   | 不允許從 Windows 進行密碼同步。 檢查全域旗標。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者： %2 |

## <a name="explanation"></a>說明  
 這個警告事件表示 Windows 已要求密碼同步，但是未設定任何全域旗標。 有兩個旗標，可讓傳送密碼至外部系統的其中一個： SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL，另一個可接收外部系統 SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB 的密碼。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

-   使用 SSO 管理 MMC 嵌入式管理單元，(系統&#124;屬性&#124;選項) 或命令列工具`ssomanage –enable winsync/extsync`若要啟用全域旗標。  

## <a name="more-info"></a>其他資訊

- **企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)
