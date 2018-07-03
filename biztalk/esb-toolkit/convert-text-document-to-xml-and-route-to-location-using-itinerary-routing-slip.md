---
title: 如何： 將文字文件轉換成 XML 和路由至檔案位置，以使用路線傳閱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01597a5f-5ca3-440e-ad97-70332233f319
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e6690af0cd326853fc0f96254aaaf7083ccd15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982567"
---
# <a name="how-to-convert-a-text-document-to-xml-and-route-to-a-file-location-using-an-itinerary-routing-slip"></a>如何： 將文字文件轉換成 XML，並路由至使用路線傳閱的檔案位置
## <a name="goal"></a>目標  
 一節示範如何建立管線以將文字文件轉換成 XML，然後選取適當的路線並將訊息路由傳送至檔案位置。  
  
 在本使用說明主題中，您將完成下列步驟：  
  
-   您可以使用管線來接收一般檔案文件，並將它轉換成 XML。  
  
-   設定路線選取器管線元件來解析適當的傳閱名單。  
  
-   建立入口匝使用自訂管線。  
  
-   以路線為基礎的一般檔案訊息路由的測試。  
  
## <a name="prerequisites"></a>必要條件  
 本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
## <a name="before-you-begin"></a>開始之前  
 您執行本使用說明主題中稍後的步驟之前，請完成下列工作：  
  
- 部署**DataFormatTransformation**路線。  
  
- 建立測試訊息。  
  
  下列程序描述如何進行每一種。  
  
#### <a name="to-deploy-the-dataformattransformation-itinerary"></a>若要部署 DataFormatTransformation 路線  
  
1.  在 Visual Studio 中，開啟 [C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation\DataFormatTransformation.sln]。  
  
2.  在 方案總管中**Itinerary.Library**專案中，按兩下**DataFormatTransformation.itinerary**在路線設計工具中開啟它。  
  
3.  在 Visual Studio 中，按一下設計介面**DataFormatTransformation.itinerary**。 在 [ **DataFormatTransformation.itinerary**屬性] 視窗中，設定下列屬性：  
  
    1.  在 **路線狀態**下拉式清單中，按一下**部署**。  
  
    2.  在 **模型匯出工具**下拉式清單中，按一下**資料庫路線匯出工具**。  
  
    3.  按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。  
  
    4.  在 **連接屬性** 對話方塊中，選擇裝載路線的存放庫資料庫中，SQL Server，然後指定 資料庫名稱 (預設名稱是**EsbItineraryDb**)。  
  
4.  儲存專案的所有成品。  
  
5.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面**DataModelTransformation**路線，，然後按一下**匯出模型**。  
  
#### <a name="to-create-the-receive-pipeline"></a>若要建立的接收管線  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下**DataFormatTransformation.Schemas**，然後按一下**屬性**。 按一下 [**應用程式**，然後輸入**GlobalBank.ESB.DataFormatTransformation.Schemas**中**組件名稱**] 方塊中。  
  
2.  以滑鼠右鍵按一下**DataFormatTransformation.Schemas**，然後按一下**屬性**。 按一下  **Signing**，然後確認**簽署組件**核取方塊已選取，而且此組件位置指向 **。\\...\\..\\..\\..\\..\keys\Microsoft.Practices.ESB.snk**。  
  
3.  以滑鼠右鍵按一下**DataFormatTransformation.Pipelines**，然後按一下**移除**。  
  
4.  以滑鼠右鍵按一下**DataFormatTransformation**，指向**新增**，然後按一下**新專案**。 按一下  **Biztalk 專案**，然後按一下**空白 Biztalk Server 專案**。 在 **名稱**方塊中，輸入**DataFormatTransformationReceive.Pipeline**。  
  
5.  以滑鼠右鍵按一下**DataFormatTransformationReceive.Pipeline**，然後按一下**屬性**。 按一下  **Signing**，然後確認**簽署組件**核取方塊已選取，而且此組件位置指向**C:\projects\Microsoft.Practices.ESB\keys\Microsoft.Practices.ESB.snk**。  
  
6.  以滑鼠右鍵按一下**DataFormatTransformationReceive.Pipeline**，指向**新增**，然後按一下**新項目**。  
  
7.  在 **加入新項目** 對話方塊中，按一下**接收管線**範本 窗格中。 在 **名稱**方塊中，輸入**ItinerarySelectReceiveFF**，然後按一下**新增**。  
  
8.  以滑鼠右鍵按一下**參考**為 DataFormatTransformationReceive.Pipeline 專案，然後按一下**加入參考**。 按一下 **專案**索引標籤，然後再按一下**DataFormatTransformation.Schemas**。 按一下 **確定**加入參考。  
  
9. 從 [工具箱] 拖曳**一般檔案解譯器**管線元件來**解譯**管線階段。  
  
10. 在 屬性 視窗的 一般檔案解譯，請按一下**DataModelTransformation.Schemas.NAOrderDocFF**中**文件結構描述**下拉式清單。  
  
11. 從 [工具箱] 拖曳**ESB 路線選取器**管線元件來**解析合作對象**管線階段。  
  
12. 從 [工具箱] 拖曳**ESB 發送器**管線元件來**解析合作對象**管線階段，然後將其下放置**ESB 路線選取器**管線元件。  
  
13. 儲存專案的所有成品。  
  
## <a name="to-create-the-test-message"></a>若要建立測試訊息  
  
1.  DataFormatTransformation.Schemas 專案 NAOrderDocFF.xsd 結構描述檔案時，按一次。 在 Visual Studio 的 [屬性] 窗格中，變更下列兩個屬性：  
  
    -   **產生執行個體輸出類型**。 按一下這個屬性，以將它變更為下拉式清單**原生**。  
  
    -   **輸出執行個體檔案名稱**。 按一下此屬性的省略符號按鈕 （...） 並接受 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation 的預設路徑。 在 **檔名**方塊中，輸入**NAOrderDocFF**，然後按一下 **儲存**。  
  
2.  以滑鼠右鍵按一下**NAOrderDocFF.xsd**下方**DataFormatTransformation.Schemas**，然後按一下**產生執行個體**。 此時，您應該有 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation 目錄中產生新的檔案。  
  
3.  複製 （不會移動） 檔案至 C:\HowTos 從 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation NAOrderDocFF.txt。  
  
    > [!NOTE]
    >  這是您將會接收並轉換為 XML 訊息。 這份文件表示 North American 訂單文件的一般檔案版本。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-deploy-the-receive-pipeline-and-the-schema"></a>若要部署的接收管線和結構描述  
  
1.  以滑鼠右鍵按一下**DataFormatTransformationReceive.Pipeline**，然後按一下**屬性**。 按一下 [**部署**，然後輸入**Microsoft.Practices.ESB**中**應用程式名稱**] 方塊中。  
  
2.  以滑鼠右鍵按一下**DataFormatTransformation.Schemas**專案，然後再按一下**屬性**。 按一下 [**部署**，然後輸入**Microsoft.Practices.ESB**中**應用程式名稱**] 方塊中。  
  
3.  關閉 [屬性] 窗格，針對**DataFormatTransformationReceive.Pipeline**並**DataFormatTransformation.Schemas**。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下**DataFormatTransformation**專案，然後再按一下**部署方案**。  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>建立和設定 ESB 匝道  
  
1.  按一下 **開始**在工作列上，指向**所有程式**，指向**BizTalk Server**，然後按一下**BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，展開**應用程式**，然後按一下**Microsoft.Practices.ESB**。  
  
3.  以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。  
  
4.  在 [**選取接收埠**] 對話方塊中，按一下**OnRamp.Itinerary**，然後按一下 **[確定]**。  
  
5.  在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.FlatFile.FILE**。  
  
6.  在 **型別**下拉式清單中，按一下**檔案**，然後按一下 **設定**。  
  
7.  在  **FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**。  
  
8.  中**FILE 傳輸屬性**對話方塊中，於**檔案遮罩**方塊中，輸入 **\*.txt**，然後按一下**確定**。  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>若要設定路線選取器管線元件  
  
1.  在 **接收位置屬性** 對話方塊中，按一下**ItinerarySelectReceiveFF**中**接收管線**下拉式清單中，然後按一下 省略符號按鈕 （...）。  
  
2.  使用**設定管線**對話方塊，即可設定下列各項**路線選取器**元件屬性：  
  
    1.  按一下  **ItineraryFactKey**屬性，然後按**Resolver.Itinerary**。  
  
    2.  按一下  **ResolverConnectionString**屬性中，輸入**路線：\\\name=DataFormatTransformation;** ，然後按一下**確定**。  
  
3.  按一下 [ **[確定]** 以關閉**接收位置屬性**] 對話方塊。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.FlatFile.FILE**接收位置，然後按一下**啟用**。  
  
#### <a name="to-test-itinerary-based-routing-of-a-flat-file-message"></a>若要測試以路線為基礎的一般檔案訊息路由  
  
1.  在 Windows 檔案總管中，瀏覽至 C:\HowTos。  
  
2.  複製 （不會移動） 到 C:\HowTos\DropFolder NAOrderDocFF.txt。  
  
3.  瀏覽至 C:\HowTos\Out。確認目錄中已寫入 DFT%MessageID%.xml 訊息。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.FlatFile.FILE**接收位置，然後按一下**停用**。  
  
5.  在後**OnRamp.Itinerary.FlatFile.FILE**接收位置已停用，以滑鼠右鍵按一下，然後按一下 **刪除**。 在 [**確認刪除接收位置**] 對話方塊中，按一下**是**。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [如何：轉換訊息，並使用路線傳閱名單將產生的訊息路由至檔案位置](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [如何：使用路線傳閱名單將單一訊息路由至多個收件者](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [訊息轉換模式](../esb-toolkit/message-transformation-patterns.md)