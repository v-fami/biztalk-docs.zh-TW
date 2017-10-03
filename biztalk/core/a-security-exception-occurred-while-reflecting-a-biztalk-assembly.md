---
title: "反映 BizTalk 組件時發生安全性例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 301b85c7-8e67-482e-8666-67a91ca5c73d
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cca28c534b910479be3ae6ad26bd1e0a27a1637d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="a-security-exception-occurred-while-reflecting-a-biztalk-assembly"></a>反映 BizTalk 組件時發生安全性例外狀況
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|反映 BizTalk 組件 "{0}" 時發生安全性例外狀況。 組件若位於共用的網路資料夾時，可能會發生此問題。 若要修正這個問題，請嘗試下列其中一種： 1。 將組件與其相依項目複製到本機電腦。 2. 調整.NET 組態的執行階段安全性原則以允許存取。|  
  
## <a name="explanation"></a>說明  
 嘗試發行不正確的.NET 原則的網路共用上的 BizTalk 組件時，會發生這個錯誤。  
  
## <a name="user-action"></a>使用者動作  
 除了錯誤訊息中所述的特定步驟，將複製本機的組件。 或編輯原則以授與完全信任近端內部網路。  
  
 **使用程式碼存取安全性原則工具 (Caspol.exe)**  
  
 您可以在使用者層級，與一般使用者權限在本機電腦上授與信任的資料夾。 若要將信任授與網路位置，您必須具有系統管理員權限，並變更電腦層級的安全性原則。 電腦原則層級做獨立於使用者原則層級，而電腦原則層級不授與完全信任給內部網路區域即使使用者原則。 原則層級必須一致。  
  
 **若要授與完全信任的本機資料夾**  
  
-   在 Visual Studio 命令提示字元中輸入下列命令：  
  
```  
caspol -u -ag All_Code -url   
C:\<FolderName>\<FolderName>\* FullTrust -n "<Name>" -d  
"<Description>"  
```  
  
 **若要授與完全信任的網路資料夾**  
  
-   在 Visual Studio 命令提示字元中輸入下列命令：  
  
```  
caspol -m -ag LocalIntranet_Zone -url   
\\<ServerName>\<FolderName>\* FullTrust -n "<Name>" -d   
"<Description>"  
```