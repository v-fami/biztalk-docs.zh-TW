---
title: 單一登入： 事件 10603 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 139d1eb5-af88-4216-9604-c052f3db13c9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 738d2939f4178fdfaa115b8dfcc2273935c37b85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270390"
---
# <a name="single-sign-on-event-10603"></a>單一登入： 事件 10603
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10603|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_DB_ACCESS|  
|訊息文字|無法存取 SSO 資料庫。 如果此狀況持續發生，SSO 服務將會移 offline.%r<br /><br /> %1.%r<br /><br /> SQL 錯誤代碼： %2|  
  
## <a name="explanation"></a>說明  
 SSO 資料庫是無法使用。  
  
## <a name="user-action"></a>使用者動作  
 請檢查警告中包含的 SQL 錯誤程式碼。 這可能會提供一些指引。 如果沒有，請連絡 Microsoft 產品支援服務。