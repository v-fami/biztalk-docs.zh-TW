---
title: "如何使用 Web 服務僅供傳訊實例中 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66873959-5b1b-4d9b-ad19-f083670420b8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ac3e87d54ab7babed8be6b4d81267d22d8ac319
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-consume-web-services-in-a-messaging-only-scenario"></a>如何在僅供傳訊實例中使用 Web 服務
SOAP 配接器的其中一項新增強功能，就是可以在僅供傳訊實例中使用根據訊息內容決定路由傳送埠來呼叫 Web 服務。 這項功能可以讓配接器直接使用 Web 服務，而不用另外建立協調流程。 這項功能也會使得 Web 服務使用效能更好，因為這時訊息並不用通過協調流程。  
  
 若要在僅供傳訊實例中使用 Web 服務，請執行下列動作：  
  
-   建立 Proxy 程式庫和 XML 結構描述來叫用 Web 服務  
  
-   設定傳送埠和接收位置來使用 Web 服務  
  
### <a name="to-create-a-proxy-library-and-xml-schemas-for-invoking-web-services"></a>若要建立 Proxy 程式庫和 XML 結構描述來叫用 Web 服務  
  
1.  決定 Web 服務的 URL。  
  
2.  開啟**空白 BizTalk Server 專案**中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案。 如需如何建立 BizTalk Server 專案的詳細資訊，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。  
  
    > [!NOTE]
    >  這個逐步解說會應用 BizTalk Server 專案，產生 Web 服務所使用的 Proxy 程式庫和 XML 結構描述。 您也可以針對相同目的.NET Framework 4.0 SDK 中使用的 Wsdl.exe 和 Xsd.exe。  
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk Server 專案名稱，然後**加入服務參考**。  
  
4.  在**加入服務參考**對話方塊中，按一下 **進階**。  
  
5.  在**服務參考設定**對話方塊中，按一下**加入 Web 參考**中**相容性**> 一節。  
  
6.  在**加入 Web 參考**對話方塊方塊中，執行下列動作：  
  
    1.  在**URL**欄位中輸入 Web 服務 URL，然後再按一下**移**。  
  
    2.  在**Web 參考名稱**欄位中，輸入命名空間的名稱，然後按一下**加入參考**。  
  
7.  Web 參考會出現在**Web 參考**方案總管 中的節點。  
  
    > [!TIP]
    >  將 web 參考加入至 BizTalk 專案中，一旦**加入 Web 參考**命令時，直接使用您以滑鼠右鍵按一下專案名稱或**參考**或**的Web參考**.  
  
8.  在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**屬性**為啟動專案設計工具。  
  
9. 在 專案設計工具中，按一下 **簽署** 索引標籤。  
  
10. 選取**簽署組件**選項，請按一下下拉式清單，如**選擇強式名稱金鑰檔**，然後按一下 **瀏覽**。  
  
11. 瀏覽並選取組件金鑰檔案，然後按一下**開啟**。  
  
12. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。  
  
13. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。  
  
### <a name="to-configure-a-send-port-and-receive-location-for-consuming-a-web-service"></a>若要設定傳送埠和接收位置來使用 Web 服務  
  
1.  在 [BizTalk Server 管理] 主控台中，建立傳送埠。 如需詳細資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 建立傳送埠時，請選取 SOAP 作為傳輸類型或傳輸通訊協定。  
  
2.  設定下列設定的 SOAP 傳送埠。 如需詳細資訊，請參閱[如何設定 SOAP 傳送埠](../core/how-to-configure-a-soap-send-port.md)。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**下列設定**|選取這個選項來指定下列屬性。|  
    |**組件名稱**|選取先前程序所建立的組件。 組件的完整的名稱會寫入至 SOAP 配接器**AssemblyName**屬性。|  
    |**型別名稱**|指定包含要叫用的 Web 方法的類別名稱。 寫入 SOAP 配接器的型別名稱**TypeName**屬性。|  
    |**方法名稱**|在清單方塊中選取其中一個方法。 Web 方法會寫入至 Soap 配接器**MethodName**屬性。|  
  
    > [!NOTE]
    >  若您要使用「根據訊息內容決定路由」(CBR)，請設定傳送埠的篩選條件。 如需詳細資訊，請參閱[如何設定傳送埠的篩選](../core/how-to-configure-filters-for-a-send-port.md)。  
  
    > [!NOTE]
    >  如果來自所叫用 Web 服務的回應訊息沒有任何訂閱者，將會產生路由失敗錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Web 服務](../core/consuming-web-services.md)