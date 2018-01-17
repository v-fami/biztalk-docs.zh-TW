---
title: "如何更新對應，使用並行的版本設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b0e377f-92ab-483e-9f3c-222c7b5ac0b1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d463823a7038e1ead7e2de323da97eda372db76
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-update-a-map-using-side-by-side-versioning"></a>如何更新對應，使用-並存版本控制
某些 BizTalk 成品，例如對應，選擇完整強式名稱 (FQSN)，在這種情況下的繫結包括使用的版本。 這可讓以並存方式，並排在兩個或多個對應[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如此一來，您可以選取其中一個輸入中的接收位置屬性的對應或輸出對應的對應中的傳送埠屬性。  
  
## <a name="prerequisites"></a>필수 구성 요소  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。  
  
### <a name="to-add-a-second-map-side-by-side-to-an-existing-map"></a>將第二個對應以並排方式加入至現有的對應  
  
1.  開啟 Visual Studio 中，及包含對應的專案。  
  
2.  開啟對應的組件，並進行程式碼變更的對應。  
  
    > [!NOTE]  
    >  如果您從協調流程，呼叫地圖和地圖參考是硬式編碼，您可能需要變更協調流程本身的程式碼。  
  
3.  變更組件的版本號碼：  
  
    1.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**。  
  
    2.  在**專案設計工具**，按一下 [**應用程式**] 索引標籤。  
  
    3.  在右窗格中，按一下 **組件資訊**。  
  
    4.  在**組件資訊**對話方塊方塊中，指定的值**組件版本**欄位來變更組件版本號碼。 您應該變更只有主要或次要版本號碼。 主要版本號碼是序列中的第一個數字 (***n***.0.0.0); 的次要版本號碼是序列中的第二位數 (0。***n*** .0.0)。  
  
    5.  按一下  **確定** 關閉 **組件資訊** 對話方塊。  
  
4.  編譯組件。  
  
5.  將組件部署到群組 （和所有的電腦）。  
  
## <a name="modifying-a-map-to-reflect-updated-version-numbers"></a>修改對應，以反映更新的版本號碼  
 .NET 組件可以叫用從對應中使用指令碼處理運算質。 這個方法可以提供很大的彈性，允許開發人員解決許多不同的自訂對應問題。 它也給對應賦予獨特的限制，就是它不只必須從內部參考組件類型名稱，同時也必須從內部參考所叫用的完整組件版本號碼。 如此一來，如果對應所呼叫的組件版本號碼變更了，所有參考該組件的連結也會一併中斷。  
  
 若要避免這個問題，我們建議如果需要從對應呼叫組件，來容納只對應功能，而這個組件的組件版本號碼固定建立特定的組件。 採用這個方法可讓您在更新其他 helper 函式的組件版本時，維持對應的關係。  
  
 如果對應所參考的組件在對應開發後產生變更，則考慮在「對應編輯器」外更新對應檔來反映更新過的版本號碼。  
  
#### <a name="to-modify-a-map-file-to-reflect-updated-version-numbers"></a>若要修改對應檔，以反映更新的版本號碼  
  
1.  使用**啟動**功能表中，開啟**記事本**。  
  
2.  在**記事本**上**檔案**功能表上，按一下 **開啟**。 在 **開啟** 對話方塊中，選取對應檔您想来修改，然後按一下 **開啟**。  
  
3.  在 [編輯] 功能表上，按一下 [尋找]。 在 **尋找** ] 對話方塊中，輸入 **組件 =**, ，然後按一下 [ **尋找下一個**。  
  
4.  如果某個外部組件含有指令碼參考的話，則「記事本」應該會找到如下列所示的 XML 項目：  
  
    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=  
    <token>  
    " Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  
  
5.  更新版本號碼。 如果有多個執行個體，請使用 **取代** 上 **編輯** 功能表。  
  
6.  儲存檔案。  
  
    > [!NOTE]  
    >  現在您可以使用「對應編輯器」來開啟對應了。