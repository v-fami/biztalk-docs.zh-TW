---
title: "連接至 Siebel 系統在 Visual Studio 使用新增配接器中繼資料精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0a82fcc-b3ac-4936-9210-03c99d3741d7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9fc38299ffdce6cf6227cacb7de0cae84b22091
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-add-adapter-metadata-wizard"></a>連接至 Siebel 系統在 Visual Studio 使用新增配接器中繼資料精靈
[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]也會公開成 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述您想要使用配接器在 Siebel 系統上執行的作業。  
  
## <a name="connecting-to-a-siebel-system-using-add-adapter-metadata-wizard"></a>連接到使用 Siebel 系統新增配接器中繼資料精靈  
 執行下列步驟來連接使用 Siebel 系統[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
#### <a name="to-connect-to-a-siebel-system"></a>連接至 Siebel 系統  
  
1.  若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：  
  
    1.  建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
    2.  以滑鼠右鍵按一下方案總管] 中的專案，指向**新增**，然後按一下 [**新增產生的項目**。  
  
    3.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
        |使用|動作|  
        |--------------|----------------|  
        |**類別**|按一下**取用配接器服務**。|  
        |**範本**|按一下**取用配接器服務**。|  
  
    4.  按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  
  
    5.  在[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取 Wcf-siebel。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  
  
        > [!IMPORTANT]
        >  如果您已經有**Wcf-siebel**通訊埠設定中的 BizTalk，請選取連接埠從**連接埠**清單。  
  
    6.  按一下 **[下一步]**。  
  
2.  從**選取繫結**下拉式清單中選取**siebelBinding**，然後按一下 **設定**。  
  
3.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**.  
  
4.  指定的使用者名稱和密碼，以連接至 Siebel 系統。  
  
5.  按一下**URI 屬性**索引標籤，然後指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  
  
    > [!NOTE]
    >  如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
6.  按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
    > [!NOTE]
    >  如果產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]且您選取現有的 WCF Siebel 傳送埠，您不需要指定繫結屬性。 繫結屬性是從傳送埠組態中挑選。 不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。 在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。  
  
7.  按一下 **[確定]**。  
  
8.  按一下 **[連接]**。 一旦建立連接之後，連線狀態會顯示為**Connected**。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。  
  
     ![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")  
  
     [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示不同的節點包含各種可以 Siebel 系統執行的作業。 例如，**商務物件**節點包含所有的商務物件和 Siebel 系統叫用的商務元件。 同樣地，**商務服務**節點包含您連接至 Siebel 系統中的所有商務服務。 如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。