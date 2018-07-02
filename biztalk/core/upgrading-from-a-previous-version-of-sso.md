---
title: 從舊版的 SSO 升級 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading, SSO
- SSO, upgrading
ms.assetid: 78b99d99-9a10-4453-9db5-ae1bacd7de50
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d12a4ee046fa7c7d835f0ddd16187e79d9d19c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979279"
---
# <a name="upgrading-from-a-previous-version-of-sso"></a>從舊版的 SSO 升級
如果您要安裝 「 企業單一登入 」 功能，而且您已經在電腦上 （例如，從 Microsoft BizTalk Server 2009) 部署舊版本，您必須完成下列步驟。  
  
1. 將 SSO 資料庫備份到安全位置  
  
2. 將主要密碼金鑰備份至主要密碼伺服器  
  
3. 更新主要密碼伺服器執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝程式，選擇**Custom Installation**，然後選取**企業單一登入**。  
  
4. 選取之後**啟用企業單一登入此電腦上**，選取**加入現有的 SSO 系統**。  
  
   您不需要從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝來更新其他的 SSO 伺服器 (非主要密碼伺服器)。 但是若您希望這類伺服器提供新的「企業單一登入」功能，您就必須使用上述的相同程序來加以更新。  
  
> [!NOTE]
>  如果您要在已安裝 Host Integration Server 2009 企業單一登入的電腦上安裝 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，且您希望更新這些伺服器，也要注意這幾項考量。  
  
 若要安裝 Host Integration Server 的電腦上其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是已安裝，請勿選取 [企業單一登入] 功能。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用主控件初始化的 SSO 功能](../core/using-host-initiated-sso-functionality.md)  
  
-   [SSO 的處理伺服器](../core/processing-servers-for-sso.md)