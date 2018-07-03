---
title: 步驟 9： 建置並部署 Echo 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ead10ab-1acf-47c5-ad16-dc6938601906
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58e0bae620c43504091c29ed2b03a33e0c7710c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980503"
---
# <a name="step-9-build-and-deploy-the-echo-adapter"></a>步驟 9： 建置並部署 Echo 配接器
![步驟 9 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")  
  
 **若要完成的時間：** 10 分鐘  
  
 在此步驟中，您將執行部署 Echo 配接器所需的工作。 這牽涉到下列各項：  
  
- 建立強式名稱檔案，並將它指派給 Echo 配接器組件  
  
- 建置 Echo 配接器  
  
- 發行至 GAC 的組件  
  
- 註冊使用 Echo 配接器 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 若要成功完成此步驟中，您應該熟悉強式名稱的檔案和 GAC。 基本的了解[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]設定是很有幫助，但並非必要。  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a>指派強式名稱給組件  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**EchoAdapter**專案，然後再按一下**屬性**。  
  
2.  在 [EchoAdapter 屬性頁] 對話方塊中，選取**簽署**從左窗格中。  
  
3.  按一下 [**簽署組件**] 索引標籤。  
  
4.  選擇**\<新...\>** 強式名稱檔案。 當系統提示輸入檔案名稱，輸入**EchoAdapter.snk**，取消選取保護我的金鑰檔使用的密碼選項，然後按一下**確定**。  
  
5.  按一下 [**應用程式**] 索引標籤。  
  
6.  變更組件名稱，使**Microsoft.Adapters.Samples.EchoV2**。  
  
7.  按一下 **檔案**Visual Studio 功能表上選擇 **全部儲存**。  
  
### <a name="to-build-and-deploy-echo-adapter"></a>若要建置並部署 Echo 配接器  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**EchoAdapter**專案，然後再按一下**建置**。 如果未成功建置，修正任何錯誤，請嘗試重建 Echo 配接器。  
  
2.  開啟 Visual Studio 命令提示字元。  
  
3.  輸入以下命令：  
  
     **gacutil.exe /if 」\<**  *assembly\Microsoft.Adapters.Samples.EchoV2.dll 路徑*  **\>"**  
  
     這會將組件安裝至 GAC，覆寫任何同名的現有組件。  
  
### <a name="to-register-the-echo-adapter-with-windows-communication-foundation"></a>若要使用 Windows Communication Foundation 註冊 Echo 配接器  
  
1. 編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。 若要這樣做，請按一下**開始**，按一下**執行**，型別**記事本\<Windows 安裝路徑\>\Microsoft.NET\Framework\\< 版本\>\CONFIG\machine.config**，然後按一下 **[確定]**。  
  
2. 更新 machine.config 檔案。 如果您的 machine.config 不包含 system.serviceModel 區段，結尾的組態檔，但在關閉根標記之前新增下一節。  
  
   > [!NOTE]
   >  取代您的配接器資訊的版本、 文化特性、 公開金鑰語彙基元和其他組件特定的資訊。  
  
   ```  
   <system.serviceModel>  
     <client>  
       <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
         name="echov2" />  
     </client>  
     <extensions>  
       <bindingElementExtensions>  
         <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
       </bindingElementExtensions>  
       <bindingExtensions>  
         <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
       </bindingExtensions>  
     </extensions>  
   </system.serviceModel>  
   ```  
  
   - 或 -  
  
     如果您的 machine.config 包含 system.serviceModel 區段，判斷哪些項目遺漏，並將其新增。  
  
   > [!NOTE]
   >  取代您的配接器資訊的版本、 文化特性、 公開金鑰語彙基元和其他組件特定的資訊。  
  
   ```  
   <client>  
     <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
       name="echov2" />  
   </client>  
   <extensions>  
     <bindingElementExtensions>  
       <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
     </bindingElementExtensions>  
     <bindingExtensions>  
       <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
     </bindingExtensions>  
   </extensions>  
   ```  
  
3. 儲存 machine.config 檔案。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此 Echo 配接器教學課程的最後一個步驟中，您將強式名稱新增至 Echo 配接器、 建置和部署配接器，然後修改 Machine.config，包含配接器的相關資訊。 此時，Echo 配接器應該可供取用端應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 完成本教學課程。 如果您想要測試的.NET 專案中的 Echo 配接器功能，請參閱[教學課程 2： 使用 Echo 配接器，從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 8： 實作 Echo 配接器的同步輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)   
 [教學課程 2：從 .NET 使用 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)