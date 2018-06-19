---
title: 與 Visual Studio 的 MSBUILD 整合 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aedcabf7-b2cf-482a-9ade-7311e104bff9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4a639945881625dd697798080c913ec0e5e3a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262830"
---
# <a name="msbuild-integration-with-visual-studio"></a>與 Visual Studio 的 MSBUILD 整合
Visual Studio 使用 MSBUILD 專案檔案格式來儲存有關受管理專案 (包含 BizTalk 專案) 的建置資訊。 透過 Visual Studio 新增及變更的專案設定會反映在為每個專案產生的 .btproj 檔案中。 Visual Studio 會使用 MSBUILD 的受主控執行個體來建置 BizTalk 專案，這表示可以在 Visual Studio 中或從命令列建置 BizTalk 專案，兩者結果都一樣。  
  
 如需 MSBUILD 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567)。  
  
 下列程序顯示如何使用 MSBUILD 從命令列建置 BizTalk 專案範例。  
  
## <a name="to-build-a-biztalk-project-from-a-command-line"></a>若要從命令列建置 BizTalk 專案  
  
1.  啟動**Visual Studio 命令提示字元**。  
  
2.  切換至專案目錄，然後執行 MSBUILD 命令以建置 BizTalk 方案。  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!NOTE]
    >  方案可以包含 BizTalk 和非 BizTalk 專案，例如 C# 類別庫。