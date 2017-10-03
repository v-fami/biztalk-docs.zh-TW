---
title: "加入和移除自訂運算質從 Visual Studio 工具箱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28f798cc-da97-4332-a842-ba87ac7b13b8
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b34d546de0bbb2a79300c4f672bdfcecdab5958
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-and-removing-custom-functoids-from-the-visual-studio-toolbox"></a>加入和移除自訂運算質從 Visual Studio 工具箱
本主題描述如何新增自訂運算質和移除自訂運算質從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。  
  
## <a name="adding-custom-functoids-to-visual-studio"></a>新增自訂運算質至 Visual Studio  
 自訂運算質必須新增至[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱，才能在對應中使用。 請使用下列程序新增自訂運算質。  
  
#### <a name="to-add-a-custom-functoid"></a>新增自訂運算質  
  
1.  新增至運算質[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。  
  
    1.  使用 [Windows 檔案總管] 找出實作自訂運算質的組件。  
  
    2.  若要將組件複製\< *BizTalk Server 安裝資料夾*>**\Developer Tools\Mapper 延伸**目錄。 BizTalk 對應工具會在此位置尋找自訂運算質。  
  
    3.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，在**工具**功能表上，按一下 **選擇工具箱項目**。  
  
    4.  在**選擇工具箱項目**對話方塊中，按一下  **BizTalk 對應工具運算質** 索引標籤。  
  
    5.  按一下**重設**，然後按一下 **確定**。 此程序會花一些時間。  
  
         您的自訂運算質現在應該出現在符合其類別之索引標籤下的工具箱中。  
  
     \- 或 -  
  
    1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，在**工具**功能表上，按一下 **選擇工具箱項目**。  
  
    2.  在**選擇工具箱項目**對話方塊中，按一下  **BizTalk 對應工具運算質** 索引標籤。  
  
    3.  按一下**重設**，然後按一下 **確定**。  
  
        > [!NOTE]
        >  如果您的自訂運算質未公開任何內嵌程式碼，請確定其組件可在全域組件快取中使用。  
  
    4.  在**檔案**功能表上，按一下 **結束**關閉[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
    5.  啟動**Visual Studio 命令提示字元**。  
  
    6.  在命令提示字元中，輸入**devenv /setup**。  
  
    7.  啟動**Microsoft Visual Studio**。  
  
         自訂運算質應該會出現在適當的索引標籤中。  
  
2.  將組件新增至全域組件快取中。 如果您的組件僅包含內嵌運算質，則可以略過此步驟。  
  
    1.  啟動**Visual Studio 命令提示字元**。  
  
    2.  切換至包含您組件的資料夾。  
  
    3.  在命令提示字元中，輸入**gacutil /if < assembly_path >**。 例如，如果組件名稱為 FunctoidLibrary.dll，則請鍵入**gacutil /if FunctoidLibrary.dll**。  
  
    4.  當您完成時，輸入**結束**。  
  
## <a name="removing-custom-functoids-from-visual-studio"></a>從 Visual Studio 移除自訂運算質  
 請使用下列程序移除自訂運算質。  
  
#### <a name="to-remove-a-custom-functoid"></a>移除自訂運算質  
  
1.  移除運算質從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。  
  
    1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，在**工具**功能表上，按一下 **選擇工具箱項目**。  
  
    2.  在**選擇工具箱項目**對話方塊中，按一下  **BizTalk 對應工具運算質** 索引標籤。  
  
    3.  尋找自訂運算質，在清單中，選取**移除**核取方塊，然後**確定**。  
  
     \- 或 -  
  
    1.  編輯在對應時[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 [**工具箱**] 索引標籤以顯示工具箱工具板。  
  
    2.  按一下包含您自訂運算質的運算質群組。  
  
    3.  以滑鼠右鍵按一下您想要移除，然後按一下 運算的質**刪除**或按下 delete 鍵。  
  
2.  移除運算質的組件從**Developer Tools\Mapper Extensions**目錄。  
  
    > [!CAUTION]
    >  如果組件包含作用中的運算質，請不要移除它。 這麼做將會中斷其他對應。  
  
    1.  啟動 Windows 檔案總管並瀏覽至**Developer Tools\Mapper Extensions**目錄[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    2.  以滑鼠右鍵按一下包含 「 移除 」 運算質的組件，然後按一下 **刪除**移除檔案。  
  
3.  從全域組件快取中移除運算質組件。 如果您的組件僅包含內嵌運算質，則可以略過此步驟。  
  
    > [!CAUTION]
    >  如果組件包含作用中的運算質，請不要將它從全域組件快取中移除。 這麼做將會中斷其他對應。  
  
    1.  啟動**Visual Studio 命令提示字元**。  
  
    2.  在命令提示字元中，輸入**gacutil /u < assembly_display_name >**。 例如，如果組件名稱為 FunctoidLibrary.dll，則請鍵入**gacutil /if FunctoidLibrary**。  
  
    3.  當您完成時，輸入**結束**。  
  
## <a name="see-also"></a>另請參閱  
 [開發自訂運算質](../core/developing-custom-functoids.md)