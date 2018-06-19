---
title: 如何啟用 ASP.NET 4.0 的已發佈 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58646ff2-77a3-49dc-8593-f6e41d85d4f3
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e68b8eef114828ad181e83ce0c7acd70a5545e0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254078"
---
# <a name="how-to-enable-aspnet-40-for-published-web-services"></a>如何啟用 ASP.NET 4.0 的已發佈的 Web 服務
在 IIS 中設定的 ASP.Net 版本。

BizTalk Server Web 服務發佈精靈依賴隨附 ASP.NET、.NET Framework 隨附的功能。 ASP.Net 版本隨附於您選擇的.NET CLR 版本。 

本主題說明如何變更.NET CLR 版本。 

## <a name="prerequisites"></a>必要條件

IIS 隨附於**網頁伺服器 (IIS)** 作業系統中的角色。 當您安裝此角色時，也選取 ASP.NET 的較新版本。 
  
## <a name="update-an-application-pool"></a>更新應用程式集區
  
1.  開啟**Internet Information Services (IIS) 管理員**:

    1. 在**伺服器管理員**，選取**工具**。
    2. 選取**Internet Information Services (IIS) 管理員**。
  
2.  展開伺服器名稱，然後選取**應用程式集區**。  
  
3.  選取的應用程式集區，並開啟**基本設定**。  
  
4. 設定 **.NET CLR 版本**至較新版本，並選取**確定**以儲存變更。  

> [!NOTE]
> 您也可以變更 web.config 檔案中的版本。
 
## <a name="allow-the-aspnet-extension"></a>允許 ASP.Net 延伸模組
  
1.  開啟**Internet Information Services (IIS) 管理員**:

    1. 在**伺服器管理員**，選取**工具**。
    2. 選取**Internet Information Services (IIS) 管理員**。
  
2.  選取伺服器名稱，然後按兩下**ISAPI 及 CGI 限制**。  
  
3. 確認 ASP.NET**允許**32 位元和 64 位元版本。  
  
## <a name="see-also"></a>另請參閱  
 [規劃發佈 Web 服務](../core/planning-for-publishing-web-services2.md)