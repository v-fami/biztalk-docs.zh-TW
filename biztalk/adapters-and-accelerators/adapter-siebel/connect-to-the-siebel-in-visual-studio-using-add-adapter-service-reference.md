---
title: "連接至 Siebel 系統在 Visual Studio 使用新增配接器服務參考外掛程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d27121be-6407-4bb6-acb5-37dc8a3785c0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 696e91d689bfc7bc058ce0c512e8fa09b91b18a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-add-adapter-service-reference-plug-in"></a>連接至 Siebel 系統在 Visual Studio 使用新增配接器服務參考外掛程式
若要連接至 Siebel 系統使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在.NET 程式設計方案，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="connecting-to-a-siebel-system-using-add-adapter-service-reference-plug-in"></a>連接到使用 Siebel 系統新增配接器服務參考外掛程式  
 執行下列步驟來連接使用 Siebel 系統[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-connect-to-a-siebel-system"></a>連接至 Siebel 系統  
  
1.  若要使用連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]BizTalk 解決方案中：  
  
    1.  建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
    2.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]隨即開啟。  
  
2.  從**選取繫結**下拉式清單中選取**siebelBinding**，然後按一下 **設定**。  
  
3.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**.  
  
4.  指定的使用者名稱和密碼，以連接至 Siebel 系統。  
  
5.  按一下**URI 屬性**索引標籤，然後指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  
  
    > [!NOTE]
    >  如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
6.  按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
7.  按一下 **[確定]**。  
  
8.  按一下 **[連接]**。 一旦建立連接之後，連線狀態會顯示為**Connected**。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。 圖形化使用者介面是相同的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
     ![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")  
  
     [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]顯示不同的節點包含各種可以 Siebel 系統執行的作業。 例如，**商務物件**節點包含所有的商務物件和 Siebel 系統叫用的商務元件。 同樣地，**商務服務**節點包含您連接至 Siebel 系統中的所有商務服務。 如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。