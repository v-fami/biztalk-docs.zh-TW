---
title: 單一登入： 事件 10851 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 582b92bf-2833-47cd-b685-1245e870d81d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdd719c77dc77fb626f97460ed92bd74ab6da812
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276542"
---
# <a name="single-sign-on-event-10851"></a>單一登入： 事件 10851
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10851|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|ENTSSO_E_PSADMIN_NO_DIRECT_PASSWORD_SYNC|  
|訊息文字|應用程式無法指派給密碼同步配接器，因為它已設定「直接密碼同步」旗標。|  
  
## <a name="explanation"></a>說明  
 應用程式無法同時使用直接密碼同步和密碼同步配接器。  
  
## <a name="user-action"></a>使用者動作  
 檢閱您的應用程式，並決定是否應該使用直接密碼同步。如果應該使用，保留旗標設定狀態，並且不要嘗試將應用程式指派至密碼同步配接器。 如果不存在，然後關閉旗標，並指派適當的密碼同步配接器應用程式。