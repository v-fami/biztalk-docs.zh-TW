---
title: 如何在本機伺服器上檢視組件和類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ddf6f60-9fef-4997-8b42-24eefd7ab0d1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c0f49559de7c4b1a13982578478cf249520479
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257318"
---
# <a name="how-to-view-assemblies-and-types-on-the-local-server"></a>如何在本機伺服器上檢視組件和類型
您可以使用「BizTalk 組件檢視工具」，檢視在本機伺服器上安裝的所有 BizTalk 組件和類型。  
  
### <a name="to-view-all-biztalk-server-assemblies-installed-in-the-gac"></a>若要檢視 GAC 中安裝的所有 BizTalk Server 組件  
  
-   若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。  
  
     安裝在電腦上全域組件快取 (GAC) 中的所有 BizTalk 組件隨即出現。  
  
     ![](../core/media/ebiz-deply-asblyvieweropenpage.gif "ebiz_deply_asblyvieweropenpage")  
組件檢視工具開啟頁面  
  
### <a name="to-view-types-attributes-and-references-for-a-biztalk-assembly"></a>若要檢視 BizTalk 組件的類型、屬性與參考  
  
1.  若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。  
  
2.  按兩下適當的組件。  
  
     在右邊窗格中會顯示 BizTalk 組件類型， 而左邊窗格中則會顯示屬性和型別。  
  
     您也可以按一下瀏覽至已安裝的組件位置**程式碼基底**左上區段的 [工作] 窗格中的連結。 (當 [Windows 檔案總管] 處於 [資料夾] 檢視模式時，無法檢視這個連結，因為資料夾清單會取代工作窗格)。  
  
### <a name="to-view-the-contents-of-a-type-in-a-biztalk-assembly"></a>若要檢視 BizTalk Server 組件中的型別內容  
  
1.  若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。  
  
2.  按兩下適當的組件。  
  
3.  在右邊窗格中，按兩下適當的型別。  
  
     **型別內容檢視器**視窗隨即開啟，並出現 XML 定義。  
  
### <a name="to-add-a-biztalk-assembly-in-the-gac"></a>若要在 GAC 中加入 BizTalk 組件  
  
1.  若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。  
  
2.  使用 [Windows 檔案總管]，巡覽到要加入至 GAC 中的組件。  
  
3.  將組件拖放至 [BizTalk 組件檢視工具] 中。  
  
     [BizTalk 組件檢視工具] 只接受 BizTalk Server 組件。 如果在檢視工具放入非 BizTalk 的組件，則會加以忽略。  
  
### <a name="to-remove-a-biztalk-assembly-from-the-gac"></a>若要從 GAC 移除 BizTalk 組件  
  
1.  若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。  
  
2.  以滑鼠右鍵按一下您想要從 GAC 並按一下 移除組的件**刪除**。  
  
### <a name="to-search-for-a-type-in-all-biztalk-assemblies"></a>若要在所有 BizTalk 組件中搜尋類型  
  
1.  若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。  
  
2.  從功能表列中，按一下  **Biztalk Server 搜尋**圖示。  
  
3.  在 [搜尋] 視窗中，指定在類型**尋找類型**下拉式清單。  
  
4.  在**BizTalk Server 組件中尋找**下拉式清單中，選取要搜尋的組件。  
  
5.  若要縮小搜尋範圍，以包含所指定的型別參考的類型，執行下列作業：  
  
    1.  按一下**進階搜尋準則**連結。  
  
    2.  在**所參考的**下拉式清單中，選取型別。  
  
    3.  按一下 **[搜尋]**。  
  
         在搜尋結果中會顯示指定的類型。  
  
         ![](../core/media/ebiz-depl-asblyviewtypes.gif "ebiz_depl_asblyviewtypes")  
BizTalk 組件類型  
  
## <a name="see-also"></a>另請參閱  
 [檢視 BizTalk 組件檢視器的組件](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)