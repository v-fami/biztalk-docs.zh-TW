---
title: 單一登入： 事件 10731 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 605e77f0-61f2-4a97-9ea0-bdc56344e8d9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10960489638aa565a11ecc32c70fc3a8fc6d477b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270686"
---
# <a name="single-sign-on-event-10731"></a>單一登入： 事件 10731
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10731|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_INVALID_USER_NOT_IN_GROUP|  
|訊息文字|無法建立對應，因為指定的使用者不是應用程式使用者帳戶的成員。%r<br /><br /> 網域名稱: %1 %r<br /><br /> 使用者名稱: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 應用程式使用者: %4 %r<br /><br /> 錯誤碼： %5|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示因為指定的使用者不是應用程式使用者帳戶的成員，不可能建立對應。  
  
 每個分支機構應用程式的應用程式使用者群組帳戶存在。 此帳戶的成員可以確認其分支機構應用程式中的認證，而且可以管理他們的認證對應的分支機構應用程式中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   將指定的使用者加入至指定的分支機構應用程式的應用程式使用者的群組。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [SSO 使用者群組](../core/sso-user-groups.md)  
  
-   [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)