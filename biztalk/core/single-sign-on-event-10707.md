---
title: 單一登入： 事件 10707 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59629786-4f98-4861-aba3-153670bafc12
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 773ba5034616742f7f63fbc90a848275587b3353
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996727"
---
# <a name="single-sign-on-event-10707"></a>單一登入： 事件 10707
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                       企業單一登入                                                                        |
| 產品版本 |                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                       |
|    事件識別碼     |                                                                                 10707                                                                                  |
|  事件來源   |                                                                                 ENTSSO                                                                                 |
|    元件    |                                                                                  N\A                                                                                   |
|  符號名稱  |                                                                        SSO_WARN_PS_NO_APP_SYNC                                                                         |
|  訊息文字   | 此配接器的密碼同步旗標必須允許密碼同步處理，而且必須符合全域旗標。 請檢查配接器旗標和全域 flags.%r<br /><br /> 配接器： %1 |

## <a name="explanation"></a>說明  
 這個警告事件表示，此配接器的密碼同步旗標必須允許密碼同步處理，且必須符合全域旗標。  

 其中一個允許傳送到外部系統 (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL) 的密碼，以便接收來自外部系統 (SSO_FLAG_PARTIAL_ 密碼的另一種密碼同步配接器的密碼同步處理會受到兩個旗標，SYNC_FROM_EXTERNAL_TO_DB)。 適用於成功進行密碼同步處理這些必須設定兩個 「 全域旗標 」 以及特定的配接器旗標。 密碼同步處理要求的外部密碼同步配接器，但任一這些旗標設定為 「 全域旗標 」 和配接器旗標時，會發出這個警告事件。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

-   使用 SSO 管理 MMC 嵌入式管理單元 (系統&#124;屬性&#124;選項) 或命令列工具`ssomanage –enable winsync/extsync`若要啟用全域旗標。  

## <a name="more-info"></a>其他資訊

- **企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  

- [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)
