---
title: 安裝錯誤訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation, error message
- error messages, installation
ms.assetid: 593b033f-03da-43ae-a948-f87aa5e4bccd
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fe3b422c860b4b697b259dc731f5484fac87455
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001807"
---
# <a name="installation-error-message"></a>安裝錯誤訊息
安裝 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 之後，定義其傳送或接收位置時，可能會產生下列錯誤：  
  
 傳訊引擎無法將接收 URL"\<傳送/接收位置 URL\>」 配接器"TIBCO EMS"。 原因:"檔案或組件名稱 TIBCO。EMS 或其相依性的其中一個是找不到。 」  
  
## <a name="possible-causes"></a>可能的原因  
 這個錯誤通常是因為下列其中一個原因造成。  
  
### <a name="assembly-not-in-gac"></a>組件不在 GAC 中  
 BizTalk Adapter for TIBCO EMS 是 .NET Framework 應用程式，因此會使用 .NET Framework 組件 TIBCO.EMS。 此組件必須位於 .NET Framework 全域組件快取 (GAC) 中，.NET Framework 在執行階段才能找到它。  
  
#### <a name="solution"></a>方案  
 若要判斷組件是否位於 GAC 中，請開啟命令提示字元，然後輸入下列命令：  
  
 `GACUTIL /L TIBCO.EMS`  
  
 如果結果沒有顯示任何項目，則您必須將組件加入至 GAC。 若要執行這項操作，請開啟命令提示字元，將目錄變更為您的 TIBCO EMS 安裝用戶端\cs 目錄 (預設安裝位置為 C:\TIBCO\EMS\Clients\CS)，然後執行下列命令：  
  
 `GACUTIL /i TIBCO.EMS.DLL`  
  
### <a name="different-version-of-assembly-in-gac"></a>GAC 中有不同版本的組件  
 TIBCO.EMS.dll 組件位於 GAC 中，但它的版本不同於用來建置 BizTalk Adapter for TIBCO EMS 的版本。 如果安裝在電腦上的 TIBCO.EMS.dll 是產品版本 4.2 (含) 以上版本，則它應該能與用來建置配接器的版本相容 (您可以向 TIBCO 確認此資訊)。  
  
#### <a name="solution"></a>方案  
 .NET Framework 已提供方法來解決這個問題。 它會呼叫*繫結重新導向*，它會使用組態檔。  
  
 請執行下列步驟來避免錯誤訊息：  
  
1. 使用任何文字編輯器開啟 BTSNTSVC.exe.config 檔案。  
  
    此檔案位於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]目錄 (預設安裝位置是： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)])。  
  
2. 為子系時，將下列項目加入至 BTSNTSVC.exe.config 檔中， \<assemblyBinding\>項目：  
  
```  
<dependentAssembly>  
    <assemblyIdentity name='TIBCO.EMS'  
        publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
    <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
        newVersion='1.0.0.0' />  
</dependentAssembly>  
```  
  
 如果沒有先前修改 BTSNTSVC.exe.config 檔案， \<assemblyBinding\>項目不會看起來像這樣：  
  
```  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
    <probing privatePath="BizTalk Assemblies;Developer  
        Tools;Tracking;Tracking\interop" />  
    <dependentAssembly>  
        <assemblyIdentity name='TIBCO.EMS'  
            publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
        <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
            newVersion='1.0.0.0' />  
    </dependentAssembly>  
</assemblyBinding>  
```  
  
1. 在命令提示字元中，輸入命令： `GACUTIL /L TIBCO.EMS`。  
  
2. 從輸出複製 TIBCO.EMS 組件版本號碼。  
  
   > [!CAUTION]
   >  兩個版本號碼會出現： 其中一個是 gacutil 公用程式的版本號碼。 您想要的後方出現的第二個版本號碼**版本 =**。  
  
3. 後面貼在 BTSNTSVC.exe.config 檔案中，引號，之間的版本號碼**newVersion =** （粗體在上述 XML 範例中的字元）。  
  
4. 儲存已修改的 BTSNTSVC.exe.config 檔。  
  
5. 重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Enterprise Message Service 疑難排解](../core/troubleshooting-tibco-enterprise-message-service.md)