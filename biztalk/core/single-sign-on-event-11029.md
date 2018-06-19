---
title: 單一登入： 事件 11029 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd7cb5b0-532c-4f50-849d-4d1644026463
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5f24cee6fcbe7db5ce0b4f31d458a5a29118c3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277190"
---
# <a name="single-sign-on-event-11029"></a>單一登入： 事件 11029
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11029|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_INFO_CASE_SENSITIVE|  
|訊息文字|SSO 資料庫區分大小寫。 SSO 伺服器會在區分大小寫的模式中執行。 請參閱 details.%r 文件|  
  
## <a name="explanation"></a>說明  
 根據預設 SSO 伺服器不會區分大小寫。 不過，SQL Server SSO 資料庫已設定為區分大小寫，因此 SSO 伺服器也會執行區分大小寫的模式。  
  
## <a name="user-action"></a>使用者動作  
 請注意這個時指定應用程式名稱和外部帳戶名稱，因為這些現在是區分大小寫。 如需詳細資訊，請參閱[SSO 伺服器](../core/sso-server.md)。