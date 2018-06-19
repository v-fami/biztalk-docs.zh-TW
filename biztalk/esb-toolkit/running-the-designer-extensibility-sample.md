---
title: 執行設計工具擴充性範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05ac3b50-5bf2-4566-8654-472391476d1f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69659359af123af7d9239241128cae06934d9a54
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007583"
---
# <a name="running-the-designer-extensibility-sample"></a>執行設計工具擴充性範例
設計工具擴充性範例會示範如何提供設計階段組態選項，對於自訂解析程式與路線服務使用兩個範例擴充項。  
  
 **若要執行設計工具擴充性範例**  
  
1.  啟動 Visual Studio。  
  
2.  在 Visual Studio 中，指向**新增**上**檔案**功能表，然後再按一下**專案**。  
  
3.  選取 [C# 類別庫] 範本類型**ItineraryLibrary**中**名稱**方塊，然後再按一下**確定**。  
  
4.  在 方案總管 中，以滑鼠右鍵按一下 ItineraryLibrary 專案，指向**新增**，然後按一下 **新的行程**。  
  
5.  在**名稱**方塊中，輸入**TestItinerary**，然後按 ENTER 鍵。  
  
6.  在工具箱中，按一下 On 遞增模型元素，然後將它拖曳至設計介面。  
  
7.  在工具箱中，按一下路線服務的模型項目上，，然後將它拖曳至設計介面。  
  
8.  在工具箱中，按一下另一個行程服務模型項目，然後將它拖曳至設計介面。  
  
9. 在工具箱中，按一下 Off 遞增模型元素，然後將它拖曳至設計介面。  
  
10. 在工具箱中，按一下 [連接器工具]，，然後拖曳之間的連線**OnRamp1**模型項目和**ItineraryService1**模型項目。  
  
11. 在工具箱中，按一下 [連接器工具]，，然後拖曳之間的連線**ItineraryService1**模型項目和**ItineraryService2**模型項目。  
  
12. 在工具箱中，按一下 [連接器工具]，，然後拖曳之間的連線**ItineraryService2**模型項目和**OffRamp1**模型項目。  
  
13. 按一下**OnRamp1**模型項目，然後再在 [屬性] 視窗中，將擴充項屬性設定為**上手 ESB 服務延伸模組**。  
  
14. 設定**BizTalk 應用程式**屬性**Microsoft.Practices.ESB**。  
  
15. 設定**接收埠**屬性**OnRamp.Itinerary**。  
  
16. 按一下**ItinearyService1**模型項目，，然後在 [屬性] 視窗中設定**Extender**屬性**範例協調流程路線服務延伸模組**。  
  
    > [!NOTE]
    >  這是安裝為設計工具擴充性範例的一部分的自訂延伸模組。 它可讓您將屬性加入至傳遞給協調流程為基礎的路線服務的屬性包。  
  
17. 設定**OtherValue**屬性**1**。  
  
18. 設定**ServiceName**屬性**Microsoft.Practices.ESB.Services.Routing**。  
  
19. 設定**SomeValue**屬性**2**。  
  
20. 以滑鼠右鍵按一下**解析程式**集合**ItineraryService1**，然後按一下 **加入新的解析程式**。  
  
21. 按一下**Resolver1**，然後在 [屬性] 視窗中，將**解析程式實作**屬性**範例解析程式擴充功能**。  
  
22. 設定**SomeResolverValue**屬性**測試**，然後將 [版本] 屬性設定為**1.0**。  
  
23. 按一下**ItineraryService2**模型項目，，然後在 [屬性] 視窗中設定**路線服務的擴充項**屬性**匝道路線服務延伸模組**.  
  
24. 設定**匝道**屬性**OffRamp1 > 傳送處理常式**。  
  
25. 按一下**OffRamp1**模型項目，，然後在 [屬性] 視窗中設定**Extender**屬性**匝道 ESB 服務延伸模組**。  
  
26. 設定**BizTalk 應用程式**屬性**GlobalBank.ESB**。  
  
27. 設定**傳送埠**屬性**DynamicResolutionOneWay**。  
  
28. 以滑鼠右鍵按一下設計介面，然後按一下**匯出模型**。  
  
29. 檢查產生的 XML。  
  
    > [!NOTE]
    >  請注意**PropertyBag**項目以及它所包含的屬性。 也請注意範例解析程式的連接字串和設定方式輸入的內容為基礎。