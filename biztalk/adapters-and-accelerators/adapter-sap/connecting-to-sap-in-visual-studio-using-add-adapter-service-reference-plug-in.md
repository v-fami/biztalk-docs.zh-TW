---
title: 在 Visual Studio 中使用連接至 SAP 新增配接器服務參考外掛程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05116c2f-08a4-495b-a031-d377e7ca33e0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31436f7835aa940b86289ae3c80c276f95e0f105
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964164"
---
# <a name="connecting-to-sap-in-visual-studio-using-add-adapter-service-reference-plug-in"></a>在 Visual Studio 中使用連接至 SAP 新增配接器服務參考外掛程式
若要連接到 SAP 系統使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在.NET 程式設計方案，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="connecting-to-an-sap-system-using-add-adapter-service-reference-plug-in"></a>連接到 SAP 系統使用新增配接器服務參考外掛程式  
 執行下列步驟來連接 SAP 系統使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-connect-to-an-sap-system"></a>若要連接至 SAP 系統  
  
1.  若要使用連接[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]BizTalk 解決方案中：  
  
    1.  建立的專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
    2.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]隨即開啟。  
  
2.  從**選取繫結**下拉式清單中選取**sapBinding**按一下**設定**。  
  
3.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。  
  
    > [!IMPORTANT]
    >  如果您使用 SAP 安全網路連線 (SNC) 程式庫連接到 SAP 系統，請勿指定使用者名稱和密碼。  
  
4.  按一下**URI 屬性**索引標籤上，指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
    > [!IMPORTANT]
    >  如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**UseSnc**連接屬性設**True**。  
  
    > [!NOTE]
    >  如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
5.  按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 例如，如果您要當做目標 ReceiveIdoc 作業您必須設定**ReceiveIdocFormat**屬性繫結至字串。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
    > [!IMPORTANT]
    >  如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**SncLibrary**和**SncPartnerName**至適當的值。  
    >   
    >  **SncLibrary**繫結屬性會使用路徑和檔名使用 SNC 連接到 SAP 系統所需的 dll。 這些 Dll 必須要有與 SAP 用戶端電腦上和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝。 如需詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南位於\<安裝指南\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
    >   
    >  **SncPartnerName**繫結屬性會採用 SNC 通訊夥伴名稱。  
  
6.  按一下 **[確定]**。  
  
7.  按一下 **[連接]**。 建立連接之後，連線狀態會顯示為**Connected**。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。 圖形化使用者介面是相同的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
     ![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")  
  
     [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]會顯示包含各種不同成品可以叫用 SAP 系統中的不同節點。 例如， **RFC**節點包含所有您連接到 SAP 系統所提供的 Rfc。 如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中連接到 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)