---
title: 單一登入： 事件 10741 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58b6b093-d136-498f-a3b5-c413150da956
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1901ad4c58f3056b74f50fead72637bc9bb8b62e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006831"
---
# <a name="single-sign-on-event-10741"></a>單一登入： 事件 10741
## <a name="details"></a>詳細資料  

|                 |                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------|
|  產品名稱   |                                 企業單一登入                                 |
| 產品版本 |                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                 |
|    事件識別碼     |                                           10741                                           |
|  事件來源   |                                          ENTSSO                                           |
|    元件    |                                            N\A                                            |
|  符號名稱  |                                SSO_WARN_SAVING_REPLAY_FILE                                |
|  訊息文字   | 正在儲存重新執行或進度 file.%r<br /><br /> 已儲存的檔案: %1 %r<br /><br /> 錯誤碼： %2 |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 會儲存重新執行或進度檔案。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  

- 使用者不必採取任何動作。  

  如需詳細資訊，請參閱下列資源：  

- [密碼同步](../core/password-synchronization2.md)
