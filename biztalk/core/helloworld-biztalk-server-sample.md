---
title: HelloWorld （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- orchestrations, messages
ms.assetid: 4416029a-ca76-45a4-b66c-b44cb71ded58
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f77c9a45e6314a4fc36fca8604677d7bd4b69098
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966607"
---
# <a name="helloworld-biztalk-server-sample"></a>HelloWorld （BizTalk Server 範例）
HelloWorld 範例示範如何使用 BizTalk 協調流程，將 XML 訊息 (訂單) 轉換為相關但不同的訊息類型 (發票)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會設定**在**做為接收位置的資料夾。 當您將檔案，例如範例檔案**SamplePOInput.xml**，到此資料夾中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用下列步驟處理訊息：  
  
1. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從接收位置資料夾擷取 XML 訂單訊息。  
  
2. 協調流程使用對應檔案，從 XML 訂單建立 XML 發票。  
  
3. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將產生的 XML 發票訊息放到傳送配接器**出**資料夾。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 在公司間的訊息交換案例中，通常必須將從交易夥伴收到的輸入訊息轉換為內部應用程式可辨識的格式。 這個範例會使用**接收**圖形，**轉換**圖形，以及**傳送**達到這個結果的圖形。 **轉換**圖形在扮演重要的角色在此範例中因為它是發生訊息格式轉換。 您拖曳**轉換**圖形至協調流程，並為其設定來源訊息、 對應名稱和目的訊息。 在執行階段，會使用您所指定的對應將來源訊息對應到目的訊息。  
  
 如需詳細資訊**轉換**圖形，請參閱[如何設定 「 轉換 」 圖形](../core/how-to-configure-the-transform-shape.md)。 如需建置對應的詳細資訊，請參閱[建立的對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\Orchestrations\HelloWorld\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|描述|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|HelloOrchestration.odx|協調訂單到發票之轉換的協調流程。|  
|HelloWorld.btproj, HelloWorld.sln|這個範例的專案及解決方案檔案。|  
|HelloWorldBinding.xml|用於自動化設定，例如連接埠繫結。|  
|InvoiceSchema.xsd, POSchema.xsd|分別是發票和訂單訊息的結構描述。|  
|POToInvoice.btm|將訂單轉換為發票的對應。|  
|SamplePOInput.xml|範例輸入檔案。|  
|Setup.bat|用來建置和初始化此範例。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-helloworld-sample"></a>建置和初始化 HelloWorld 範例  
  
1. 在命令視窗中，瀏覽至下列資料夾：  
  
    \<*範例路徑*\>\Orchestrations\HelloWorld  
  
2. 執行檔案 Setup.bat，這會執行下列動作：  
  
   - 在下列資料夾中為這個範例建立輸入 (In) 和輸出 (Out) 資料夾：  
  
      \<*範例路徑*\>\Orchestrations\HelloWorld  
  
   - 為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
   - 建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置以及傳送埠和接收埠，並將其繫結至協調流程。  
  
   - 啟用接收位置並啟動傳送埠。 登錄和啟動協調流程。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。 您可檢視事件記錄進行確認。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-helloworld-sample"></a>執行 HelloWorld 範例  
  
1.  Samplepoinput 檔的複本貼到**在**資料夾。  
  
2.  觀察中建立的.xml 檔案**出**資料夾。 此檔案包含從輸入檔案 SamplePOInput.xml 建構的 XML 發票。 這個檔案的名稱的格式\< *MessageID*\>.xml，其中*\<MessageID\>* 會產生來唯一識別該訊息的 GUID.  
  
## <a name="uninstalling-this-sample"></a>解除安裝這個範例  
  
#### <a name="to-uninstall-the-helloworld-sample"></a>解除安裝 HelloWorld 範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Orchestrations\HelloWorld\  
  
2.  執行 Cleanup.bat。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程 (BizTalk Server Samples 資料夾)](../core/orchestrations-biztalk-server-samples-folder.md)