---
title: 單一登入： 事件 10565 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d279491-dc0d-44c4-a77e-a67498a3481d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9567421210689d8615cf88e7fbd6493ef5749d02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271030"
---
# <a name="single-sign-on-event-10565"></a>單一登入： 事件 10565
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10565|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_ERROR_SECRET_VALIDATE_FAILED|  
|訊息文字|無法從登錄載入密碼。 SSO 服務的服務帳戶變更或密碼可能已損毀。 從備份 file.%r 還原密碼<br /><br /> MSID: %1|  
  
## <a name="explanation"></a>說明  
 有可能，系統中的系統管理員已變更為 SSO 服務帳戶，讓無法解密。  
  
## <a name="user-action"></a>使用者動作  
 尋找變更 SSO 服務帳戶的人員，然後從備份檔案還原密碼。 如需有關還原密碼的詳細資訊，請參閱[管理主要密碼](../core/managing-the-master-secret.md)。