---
title: 單一登入： 事件 10740 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e8521e7-32af-4a58-8b1a-66ea1d13f1e1
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9bf7c2cdaae3cffe280035f007cd1b49d2c70c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970055"
---
# <a name="single-sign-on-event-10740"></a>單一登入： 事件 10740
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                 企業單一登入                                                                  |
| 產品版本 |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                 |
|    事件識別碼     |                                                                           10740                                                                            |
|  事件來源   |                                                                           ENTSSO                                                                           |
|    元件    |                                                                            N\A                                                                             |
|  符號名稱  |                                                               SSO_WARN_INVALID_WINDOWS_USER                                                                |
|  訊息文字   | 對應用程式 update.%r 的 Windows 帳戶無效<br /><br /> 應用程式名稱: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 錯誤碼： %3 |

## <a name="explanation"></a>說明  
 這個警告事件表示 （事件訊息中指定） 的 Windows 帳戶不是有效的應用程式更新。 變更主機群組應用程式的 Windows 帳戶時，可能發生這項目。 主機群組應用程式可讓單一登入外部系統的 Windows 系統。 它們可以將一組外部的使用者對應至單一的 Windows 帳戶。 它們會對應至 Windows 帳戶被定義應用程式的 [應用程式使用者] 欄位中。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 檢查 Windows 帳戶已使用無效。  

- 重新建立具有正確的 Windows 帳戶屬性的 Windows 帳戶。  

  如需詳細資訊，請參閱下列資源：  

- [密碼同步](../core/password-synchronization2.md)
