---
title: 安裝 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41b9b34b-3fbb-480f-a335-a218eab33693
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95fba9830bd97dd619cd16d18c0363a4525d1397
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999703"
---
# <a name="install-the-wcf-lob-adapter-sdk"></a>安裝 WCF LOB 配接器 SDK
安裝和設定[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。 

## <a name="requirements"></a>需求 
安裝下列元件安裝在系統上[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 

> [!NOTE]
> **如需支援版本的清單**，請參閱： 
> 
> [BizTalk Server 2016 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
> [BizTalk Server 2013 和 2013 R2 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)

|                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                         Windows                                          | x86 或 x64 <br/><br/>所需的 OS 資源包括：<br/> <ul><li>支援 OleTx 異動時所需的 Microsoft Distributed Transaction Coordinator (MSDTC):</li><li>支援可靠傳訊所需的訊息佇列 (MSMQ):</li><li>如果您想要裝載在 IIS 中的應用程式所需的 Internet Information Services (IIS):</li><li>如果您想要裝載在 WAS 中的應用程式所需的 Windows Process Activation Service (WAS):</li></ul> |
|                             Windows Communication Foundation                             |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|        [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)]        |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|       [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]       |                                                                                                                                     如果您正在建置自訂的配接器，或開發使用配接器的方案建置所需[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。                                                                                                                                      |
| [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] |                                                                                                                                                                 如果您使用與配接器所需[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。                                                                                                                                                                 |

## <a name="install"></a>安裝

> [!IMPORTANT]
> * 關閉所有 Visual Studio 執行個體
> * 若要執行**完成**安裝程式，確認已在電腦上安裝 BizTalk Server。  

1. 執行[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe**以系統管理員身分。

2. 選取 **安裝 Microsoft BizTalk Adapters**，然後選取**安裝 Microsoft WCF LOB 配接器 SDK**。  

3. 在 [**歡迎**畫面上，選取**下一步]**。  

4. 接受授權合約，然後選取 [下一步]。  

5. 在 **選擇 安裝類型**，選取安裝類型：  

   -   若要安裝的通用執行的階段和工具，請選取**典型**。  

   -   若要選取您想要安裝的安裝位置的功能，請選取**自訂**，然後選取您想要安裝的功能。  

   -   若要安裝所有功能，請選取**完成**。  

6. 選取 [安裝]。  

## <a name="update-or-remove"></a>更新或移除

1. 開啟**程式和功能**。 

2. 在清單中，選取**Windows Communication Foundation LOB 配接器 SDK**，然後選取**變更**。  

3. 在 [**歡迎**畫面上，選取**下一步]**。  

4. 執行下列其中之一：  

   - 若要選取您想要安裝的元件，請選取**變更**。  

   - 若要修復最近安裝中的錯誤，請選取**修復**。  

   - 若要移除[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]從電腦中，選取**移除**。  

5. 如果您選擇修改安裝：  

   1.  選取 **[下一步]**。  

   2.  選取 **變更**，然後選取**完成**。  

6. 如果您選擇修復安裝，在**準備好修復 WCF LOB 配接器 SDK**對話方塊中，選取**修復**，然後選取**完成**。  

7. 如果您選擇要移除介面卡，在**即可移除 WCF LOB 配接器 SDK**對話方塊中，選取**移除**，然後選取**完成**。  


#### <a name="remove-custom-adapters-after-uninstalling-the-wcf-lob-adapter-sdk"></a>移除自訂配接器之後解除安裝 WCF LOB 配接器 SDK  

 如果您在開發的任何自訂的配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，而且您已在電腦上註冊這些配接器，您還必須完成下列程序。  

1.  從全域組件快取 (GAC) 中移除自訂配接器。  

    1.  開啟**Visual Studio 命令提示字元**。  

    2.  移除自訂**配接器.dll**從 GAC using**命令 gacutil /u**。  

2.  移除 machine.config 中的自訂配接器繫結的參考  

    1.  移至 machine.config 檔名\<*系統磁碟機*\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。  

    2.  使用文字編輯器中開啟檔案。  

    3.  搜尋項目 bindingExtensions、 用戶端和 bindingElementExtensions system.serviceModel\extensions 底下。  

    4.  移除屬於您自訂的配接器的 WCF 繫結。  

## <a name="do-a-silent-installation"></a>執行無訊息安裝  
 無訊息安裝適合的測試案例或大型企業部署的一部分。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] 提供命令列參數，您可以搭配 AdapterFramework.msi 執行無訊息安裝。  

> [!NOTE]
>  若要執行無訊息安裝，您應該在電腦上的系統管理員。 


1. 以系統管理員身分開啟命令提示字元。  

2. 輸入以下內容：

   ```  
   AdapterFramework.msi /quiet MUOPTIN=”Yes”  
   ```  

   AdapterFramework.msi 搭配使用下列命令列選項：  

   * 使用`/quiet`安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]以無訊息模式。  

   * 使用 MUOPTIN=[0|1 = [是]&#124;[否]，來指示是否[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]應該檢查 Microsoft update 的更新。  

       當設定為 [是]，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]檢查透過 Microsoft Update 的更新。 若設為 no[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不會檢查 Microsoft update 的更新。  

> [!NOTE]
>  若要顯示的命令列安裝的其他選項，請輸入`AdapterFramework.msi /?`在命令提示字元。  

