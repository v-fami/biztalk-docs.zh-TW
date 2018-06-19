---
title: 建置和測試配接器專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b5eb486-99ae-4661-b0d0-d2d363d97b73
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dddde1681ab95a4c1fe7b762d7608cac33580411
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233054"
---
# <a name="build-and-test-the-adapter-project"></a>建置和測試配接器專案
若要測試對 AdapterManagement 專案進行的所有變更，請重新建置該專案。 建置成功後，執行「新增配接器中繼資料精靈」，確認已將所有的內部及外部 XSD 檔案加入 AdapterManagement 專案。 如需使用 新增配接器中繼資料精靈的指示，請參閱[如何新增至 BizTalk 專案的配接器中繼資料](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md)。  
  
 若要測試的組態結構描述所做的變更，開啟每一個 XSD 檔案，以確保它會要求輸入並接受正確的資料所產生的屬性頁。 您可以設定傳送埠、 接收位置、 傳送處理常式和接收處理常式中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 **。**  
  
> [!NOTE]
>  配接器可能只有部分的組態結構描述。 例如，不支援接收訊息的傳送配接器可能只有 TransmitLocation.xsd 和 TransmitHandler.xsd 結構描述。  
  
### <a name="to-test-the-transmitlocationxsd-file"></a>測試 TransmitLocation.xsd 檔案  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **BizTalk Server 管理**。  
  
2.  展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**] 節點，展開 [ **BizTalk 群組**，依序展開**傳送埠**節點，指向**新增**，和然後按一下**靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入傳送埠的名稱。 展開**傳輸**節點，然後再選取**主要**節點。  
  
4.  在右窗格中，在**傳輸類型**方塊中，選取**靜態**，然後按一下**設定**。 顯示的畫面應該會包含您在 TransmitLocation.xsd 檔案中指定的欄位。  
  
### <a name="to-test-the-receivelocationxsd-file"></a>測試 ReceiveLocation.xsd 檔案  
  
1.  展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**] 節點，展開 [ **BizTalk 群組**，依序展開**接收埠**集合中，展開新建立的接收埠或以滑鼠右鍵按一下您要新增接收位置，接收埠**接收位置**集合中，指向**新增**，然後按一下**單向接收位置**.  
  
2.  在**選取接收埠**對話方塊方塊中，選取連接埠。  
  
3.  在**接收位置屬性**對話方塊的左窗格中，選取**一般**節點。  
  
4.  在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入接收位置的名稱。  
  
5.  在**接收位置屬性**對話方塊，在右窗格中，在**傳輸類型]** 方塊中，選取**靜態**，然後按一下 [**設定**. 顯示的畫面應該會包含您在 ReceiveLocation.xsd 檔案中指定的欄位。  
  
### <a name="to-test-the-receivehandlerxsd-file"></a>測試 ReceiveHandler.xsd 檔案  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **BizTalk Server 管理**。  
  
2.  展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**] 節點，展開 [ **BizTalk 群組**展開**平台設定**，依序展開**配接器**，按一下**靜態**，然後按一下 **BizTalkServerApplication**的方向與**接收**。  
  
3.  在 [結果] 窗格中，接收處理常式，以滑鼠右鍵按一下，然後按一下**屬性**。 在**一般**索引標籤上，按一下 **屬性**。 顯示的畫面應該會包含您在 ReceiveHandler.xsd 檔案中指定的欄位。  
  
### <a name="to-test-the-transmithandlerxsd-file"></a>測試 TransmitHandler.xsd 檔案  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**靜態**，然後按一下 **BizTalkServerApplication**的方向與**傳送**。  
  
2.  在 [結果] 窗格中，接收處理常式，以滑鼠右鍵按一下，然後按一下**屬性**。 在**一般**索引標籤上，按一下 **屬性**。 顯示的畫面應該會包含您在 TransmitHandler.xsd 檔案中指定的欄位。