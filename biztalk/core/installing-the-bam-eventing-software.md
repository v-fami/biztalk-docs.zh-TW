---
title: "安裝 Bam-eventing 軟體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3638d34-f5a8-4ffd-99eb-d38aed4c0732
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c41606f6056dcc4edb90b4db5ef6a41901835b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-bam-eventing-software"></a>安裝 BAM-Eventing 軟體
若要使用 BAM-Eventing API 來實作 BAM 方案，或是設定您的 Windows Workflow Foundation 或 Windows Communication Foundation 應用程式來使用 Windows Workflow Foundation 適用的 BAM 攔截器，您必須使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式來安裝 BAM-Eventing 軟體。 這個軟體可以安裝為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段的一部分，或是在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝應用程式中選取 [其他軟體] 底下的 [BAM Eventing Support] 來個別安裝。  
  
### <a name="to-install-the-bam-eventing-software"></a>若要安裝 BAM-Eventing 軟體  
  
1.  使用具有系統管理員權限的帳戶登入將裝載 WF 應用程式的電腦。  
  
2.  執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝光碟上的安裝程式。  
  
3.  清除所有選取的選項。 如果您不執行這個步驟，您可能會安裝您不需要的軟體。  
  
4.  展開**其他軟體**，然後選取**Bam-eventing**核取方塊。  
  
5.  按一下 **[下一步]**。  
  
6.  按一下 **[安裝]**。  
  
7.  完成安裝程序時，按一下**確定**。  
  
     BAM-Eventing 軟體現在已經安裝好了。  
  
> [!NOTE]
>  使用這個方法安裝 BAM 攔截器程式庫不需要購買額外的授權。  
  
 如果您對於監控 BAM 攔截器的效能計數器資料感興趣，您必須先使用 InstallUtil.exe 進行註冊。  
  
### <a name="to-register-bam-interceptor-performance-counters-by-using-installutilexe"></a>若要使用 InstallUtil.exe 註冊 BAM 攔截器效能計數器  
  
1.  啟動**[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元**身為系統管理員。  
  
2.  在命令提示字元中，輸入下列命令：  
  
     InstallUtil [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\Microsoft.BizTalk.Bam.Interceptors.dll  
  
3.  型別**結束**，然後按 ENTER 關閉命令提示字元。  
  
     現在就可以使用 BAM 攔截器效能計數器。  
  
> [!NOTE]
>  根據預設，只有系統管理員和某些系統帳戶才有記錄效能資料的權限。 若要在 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上啟用存取，請將用來執行工作流程應用程式的帳戶加入到 Performance Log Users 群組。  
  
## <a name="see-also"></a>另請參閱  
 [實作 BAM 解決方案](../core/implementing-bam-solutions.md)   
 [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)