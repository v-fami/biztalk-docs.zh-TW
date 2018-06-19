---
title: 單一登入： 事件 11008 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7e11dbc-7596-45fa-ae54-a6e79498e60e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88d2dfa2cfb71d66b43cfaa77b24b1dfce70fd7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276902"
---
# <a name="single-sign-on-event-11008"></a>單一登入： 事件 11008
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11008|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_CHECK_GROUP|  
|訊息文字|檢查群組成員資格 failed.%r<br /><br /> 群組名稱: %1 %r<br /><br /> 帳戶名稱: %2 %r<br /><br /> 其他資料: %3 %r<br /><br /> 錯誤碼： %4|  
  
## <a name="explanation"></a>說明  
 這可能是因為網路問題、 跨網域使用或混合層級的網域控制站 (例如，如果您的系統使用的網域控制站，同時從[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]和[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)])。  
  
## <a name="user-action"></a>使用者動作  
 請洽詢您的網路系統管理員，以查看是否有任何網路問題，或如果您的系統具有任何跨網域使用或的網域控制站的混合層級。