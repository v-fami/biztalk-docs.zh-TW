---
title: 配接器登錄檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6750f0ed-4411-4a63-a7fe-f66132cd1e22
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7212cb1cbd370e0b7df04a11744d176c126c39ac
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826470"
---
# <a name="adapter-registration-file"></a>配接器登錄檔案
順利建立自訂配接器程式碼之後，必須向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 註冊。 若要執行此作業，可將登錄更新為適當配接器設定。 您可以手動寫入登錄檔案，但由於輸入精確和複雜資訊容易發生錯誤， 更好的選擇是要執行配接器登錄精靈。 配接器登錄精靈 」 可讓您所有相同選項從從頭開始建立登錄檔，並降低檔案中的錯誤。 如需配接器登錄精靈 」 的詳細資訊，請參閱[配接器登錄精靈](../core/adapter-registry-wizard.md)。  
  
 StaticAdapterManagement.reg 和 DynamicAdapterManagement.reg 檔案位於 \microsoft *\<磁碟機\>*: \Program Files\Microsoft BizTalk Server\SDK\Samples\AdaptersDevelopment\File 配接器。 當您執行其中一個檔案 (您可以按兩下或以滑鼠右鍵按一下並選取**合併**)，它向登錄註冊範例 file 配接器，並安裝到全域組件快取的組件。 若要註冊自訂配接器的最佳選項是使用配接器登錄精靈 建立新的登錄檔。 如果自訂靜態配接器與範例配接器相似，並且您決定修改現有的登錄檔案，請開啟 StaticAdapterManagement.reg 檔案並修改下列屬性：  
  
-   **條件約束**  
  
-   **InboundTypeName**  
  
-   **InboundAssemblyPath**  
  
-   **OutboundTypeName**  
  
-   **OutboundAssemblyPath**  
  
-   **AdapterMgmtTypeName**  
  
-   **AdapterMgmtAssemblyPath**  
  
-   **PropertyNameSpace**  
  
> [!NOTE]
>  針對**OutboundAssemblyPath**並**AdapterMgmtAssemblyPath**我們建議您包含您的本機路徑中屬性值，因為組態可能會中斷時安裝在不同伺服器位置。 更好的選擇是使用強式名稱，並將它安裝在全域組件快取中。  
  
 有兩個選擇可指定實作配接器接收器、配接器傳輸器和配接器管理的 .NET 類型：  
  
1. 配接器安裝至資料夾，並指定\*TypeName 和\*AssemblyPath 其中\*TypeName 是型別。此類別的完整名稱和\*AssemblyPath 是組件的路徑和檔案名稱。  
  
2. 在全域組件快取中安裝配接器，只指定 * TypeName 其中\*TypeName 是型別。AssemblyQualifiedName 的類別。 這是建議選項。  
  
   所有配接器都必須具有下列指定之 GUID 的登錄機碼：  
  
- **實作類別\\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}**  
  
- **「 InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"**  
  
- **「 OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"**  
  
- **「 ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"**  
  
- **「 TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"**  
  
  對於傳送和接收處理常式以及位置屬性頁，以配接器架構為基礎的配接器都必須使用這些特定的 GUID。 請注意，是否配接器是僅限傳送配接器只需要**OutboundProtocol_PageProv**並**TransmitLocation_PageProv**Guid。 同樣地僅接收配接器只是需要**InboundProtocol_PageProv**並**ReceiveLocation_PageProv** Guid。  
  
  下列程式碼來自 StaticAdapterManagement.reg 檔案，而來自 DynamicAdapterManagement.reg 檔案的程式碼幾乎完全相同。 如需每個登錄屬性的詳細資訊，請參閱[註冊配接器](../core/registering-an-adapter.md)。 變更登錄檔案之後，請儲存並執行檔案。  
  
```  
Windows Registry Editor Version 5.00  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}]  
@="Static DotNetFile Adapter"  
"AppID"="{12A6EBAA-CF68-4B58-B36E-A5A19B22C04E}"  
  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\BizTalk]  
@="BizTalk"  
"TransportType"="Static DotNetFile"  
"Constraints"=dword:00003C0b  
  
"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"  
"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"  
"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"  
"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"  
  
"InboundEngineCLSID"="{3D4B599E-2202-4bbb-9FC6-7ACA3906E5DE}"  
"InboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileReceiver""InboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll"  
"OutboundEngineCLSID"="{024DB758-AAF9-415e-A121-4AC245DD49EC}"  
"OutboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileTransmitter""OutboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll""AdapterMgmtTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.Designtime.StaticAdapterManagement""AdapterMgmtAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Design Time\\Adapter Management\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Designtime.dll""PropertyNameSpace"="http://schemas.microsoft.com/BizTalk/2003/SDK_Samples/Messaging/Transports/dotnetfile-properties"  
"AliasesXML"="<AdapterAliasList><AdapterAlias>DotNetFILE://</AdapterAlias></AdapterAliasList>"  
"ReceiveHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"ReceiveLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories]  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}]  
```  
  
### <a name="to-register-the-static-sample-adapter"></a>若要註冊靜態範例配接器  
  
1. 請完成下列程序，以執行 SDK 中的 FILE 配接器範例。 如需詳細資訊，請參閱 < [File 配接器 （BizTalk Server 範例）](../core/file-adapter-biztalk-server-sample.md)。  
  
2. 按一下 **開始**，指向**所有程式**，指向**附屬應用程式**，然後按一下**Windows 檔案總管**。  
  
3. BizTalk Server 中，瀏覽至安裝磁碟機，然後瀏覽 **<**`drive`**>: \Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\SDK\Samples\AdaptersUsage\File 配接器**。  
  
4. 若要將範例配接器新增至登錄中，按兩下**StaticAdapterManagement.reg**。(如果您想要將動態 file 配接器新增至登錄，請執行**DynamicAdapterManagement.reg**改為與 everywhere 檔案其他適當的使用。)  
  
   > [!NOTE]
   >  如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不是安裝在電腦的磁碟機 C，您必須將 StaticAdapterManagement.reg 檔案修改為正確的安裝路徑。 搜尋檔案 c： 和它取代成正確的安裝磁碟機。  
  
5. 在**登錄編輯程式** 對話方塊中，按一下**是**以將範例配接器新增至登錄，然後按一下**確定**以關閉對話方塊，確認資訊。新增至登錄。  
  
6. 若要在關閉 Windows 檔案總管中，**檔案**功能表上，按一下**關閉**。  
  
    現在範例靜態配接器已經在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中註冊。
