---
title: "單一登入： 事件 10611 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4549ac01-b828-478f-aea0-862e14fac149
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3582ee070b960b7eb17facc8d48e0b3e11dc5b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10611"></a>單一登入： 事件 10611
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10611|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_INFO_SERVICE_STARTING_NO_SSL|  
|訊息文字|SSO 服務正在 starting.%r<br /><br /> 電腦名稱: %1 %r<br /><br /> SQL Server 名稱: %2 %r<br /><br /> SSO 資料庫名稱: %3 %r<br /><br /> 不使用 SSL。 有關如何保護 SQL Server 連接，請參閱文件以取得詳細資料。|  
  
## <a name="explanation"></a>說明  
 ENTSSO 服務正在啟動而不需要使用安全通訊端層 (SSL)。 建議您從 SSO 服務保護您的連線，為 SQL。  
  
## <a name="user-action"></a>使用者動作  
 請參閱文件，網址[如何針對 SSO 啟用 SSL](../core/how-to-enable-ssl-for-sso.md)  
  
 執行個體時提供 SQL Server 登入。