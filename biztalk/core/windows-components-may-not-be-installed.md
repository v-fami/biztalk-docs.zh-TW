---
title: "可能未安裝 Windows 元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc78ac0a-ee21-4633-afb3-1357efd29903
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506f9c310a75c9f65564e4feb047157731bafa66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="windows-components-may-not-be-installed"></a>Windows 元件可能無法安裝
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|下列 Windows 元件可能未安裝： 應用程式伺服器-&gt;網際網路資訊服務 (IIS)-&gt;共同檔案。|  
  
## <a name="explanation"></a>說明  
 沒有網際網路資訊服務 (IIS) 安裝在本機電腦上嘗試發佈時，會發生這個錯誤。  
  
## <a name="user-action"></a>使用者動作  
 Windows 7 和 Windows Vista SP2 中，將 IIS 安裝在本機電腦，並將 IIS 設定，如下所示：  
  
1.  按一下**啟動**，按一下 **控制台**，然後按一下**程式**。  
  
2.  按一下**開啟或關閉 Windows 功能**。 [Windows 功能精靈] 隨即出現。  
  
3.  若要新增，請核取 IIS 元件。  
  
 如[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]和[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，將 IIS 安裝在本機電腦，並將 IIS 設定，如下所示：  
  
1.  按一下**啟動**，按一下 **控制台**，然後按一下**系統管理工具**。  
  
2.  按一下**伺服器管理員**。 [伺服器管理員] 視窗隨即出現。  
  
3.  按一下**新增角色**，新增角色精靈 隨即出現。  
  
4.  若要新增，請選取 IIS 元件。