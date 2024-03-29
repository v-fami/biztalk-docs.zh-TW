---
title: 單一登入： 事件 10718 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de075c59-8396-48d1-be55-79303f83f984
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 958753d50d15662cd138ea5460c121eefcac8a98
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004983"
---
# <a name="single-sign-on-event-10718"></a>單一登入： 事件 10718
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                     企業單一登入                                                                     |
| 產品版本 |                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                     |
|    事件識別碼     |                                                                               10718                                                                               |
|  事件來源   |                                                                              ENTSSO                                                                               |
|    元件    |                                                                                N\A                                                                                |
|  符號名稱  |                                                                SSO_ERROR_REPLAY_INCORRECT_ADAPTER                                                                 |
|  訊息文字   | 重新執行或進度 file.%r 中偵測到損毀<br /><br /> 檔案名稱: %1 %r<br /><br /> 清除配接器名稱: %2 %r<br /><br /> 解密的配接器名稱： %3 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示在重新執行或進度檔案中偵測到損毀。  

 因此它可以用來播放該特定的配接器為特定的密碼同步配接器會儲存重新執行檔案。 配接器名稱會儲存在清除加密形式。 此訊息表示，當重新執行檔案已解密播放解密的配接器名稱不符合配接器名稱。 這可以建議已部分損毀或可能遭竄改的重新執行檔案。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 判斷為什麼重新執行檔案的內容可能已修改，請參閱備份是否存在。  

- 請檢查 SSO 主要密碼是否已變更或 SSO 服務帳戶已變更，這可能會影響加密行為。  

- 刪除重新執行檔案。  

  如需詳細資訊，請參閱下列資源：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
