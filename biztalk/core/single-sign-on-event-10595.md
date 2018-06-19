---
title: 單一登入： 事件 10595 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1517478c-7217-4e34-a5cb-ff7deea367ed
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9139eb7479b0a048e2fab197863b42c47f87992a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271262"
---
# <a name="single-sign-on-event-10595"></a>單一登入： 事件 10595
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10595|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_APP_INCOMPLETE_FIELDS|  
|訊息文字|無法啟用應用程式，因為欄位不完整 application.%r<br /><br /> 應用程式名稱: %1 %r<br /><br /> 定義的欄位數目: %2 %r<br /><br /> 建立的欄位數目： %3|  
  
## <a name="explanation"></a>說明  
 在建立時應用程式的應用程式開發介面層級，您可以指定的欄位 （也就是使用者識別碼，密碼） 會定義應用程式數目。 也會建立每個已定義的欄位。 這則警告訊息會列出應用程式名稱、 定義的欄位數目和建立的欄位數目。  
  
## <a name="user-action"></a>使用者動作  
 決定哪些欄位所定義，但不是會建立，然後返回，並建立它們。