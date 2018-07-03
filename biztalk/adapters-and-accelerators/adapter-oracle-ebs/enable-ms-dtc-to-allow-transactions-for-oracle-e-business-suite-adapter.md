---
title: 啟用 MS 分散式交易協調器，以允許異動 for Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 634538e5-7292-4b3f-85b0-c6db86d0dbd2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53037e9a7dc1ccc3c0ef21860696060ad1c046a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984991"
---
# <a name="enable-ms-distributed-transaction-coordinator-to-allow-transactions-for-oracle-e-business-suite"></a>啟用以允許異動 for Oracle E-business Suite 的 MS 分散式交易協調器
設定 MSDTC，才能開始建立應用程式使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
使用 Oracle E-business Suite 作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型或 WCF 通道模型) 可以在交易範圍內執行。 如果用戶端程式會有一個以上的交易式資源作為相同交易的一部分，取得更高為 MSDTC 交易的交易。 若要啟用配接器來執行 MSDTC 交易的範圍內的作業，請執行的電腦上設定 MSDTC [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，並在 Oracle E-business Suite。 此外，將 MSDTC 例外狀況清單在防火牆中，這可能是內建的 Windows 防火牆。 
  
> [!NOTE]
>  設定 MSDTC 的步驟因不同作業系統而異。 本主題中列出的步驟適用於 Windows 用戶端和 Windows Server 作業系統。  
  
## <a name="configure-msdtc"></a>設定 MSDTC  
  
1. 開啟**元件服務**。  

   或者，在**伺服器管理員**，選取**工具**，然後選取**元件服務**。  
  
2. 依序展開**Microsoft.biztalk.deployment.deployercomponent**，展開**電腦**，展開**我的電腦**，展開**分散式交易協調器**，以滑鼠右鍵按一下**本機 DTC**，然後選取**屬性**。  
  
3. 選取 **[安全性]** 索引標籤。在此索引標籤中，選取下列各項： 

   - **網路 DTC 存取**
   - **允許遠端用戶端** 
   - **允許輸入** 
   - **允許輸出** 
   - **沒有所需的 Authetnication**
  
4. 選取 [確定] 儲存您的變更。  
  
5. 如果系統提示重新啟動 MSDTC 服務，請選取**是**。 重新啟動 MSDTC 服務之後，關閉 [屬性和元件服務] MMC。 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a>加入 Windows 防火牆例外清單中的 MSDTC  

> [!TIP] 
>  Microsoft 分散式 Tansaction 協調器 (MSDTC) 可能已允許在防火牆中。 如果是的話，它會列為輸入規則。 如果未列出，請使用本節以允許 MSDTC。 

1.  開啟**Windows 防火牆**，然後選取**進階設定**左側。  

    或者，在**伺服器管理員**，選取**工具**，然後選取**具有進階安全性的 Windows 防火牆**。  
  
2.  以滑鼠右鍵按一下**輸入規則**，然後選取**新規則**。  
  
3.  在精靈中： 

    1. 選取 [**計劃**，然後選取**下一步]**。 
    2. 設定**程式路徑**要`%SystemRoot%\system32\msdtc.exe`，然後選取**下一步**。  
    3. **允許連線**，然後選取**下一步**。
    4. 選取 [**網域**，然後選取**下一步]**。
    5. 輸入任何名稱，例如`MSDTC for Oracle EBS`，然後選取**完成**。
  
5.  完成精靈，並關閉 Windows 防火牆。 
  
## <a name="next"></a>下一個 
[適用於 Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)