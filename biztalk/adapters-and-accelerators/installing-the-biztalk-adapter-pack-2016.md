---
title: 安裝 BizTalk Adapter Pack 2016 |Microsoft Docs
description: 以無訊息模式安裝的 BAP 2016，32 位元與 64 位元、 一般或自訂安裝
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f3e1717-8063-4460-bfdc-a933cd58a5c1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6eef8511564f134f96745667b94f69f6fb263e17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000383"
---
# <a name="install-the-biztalk-adapter-pack-2016"></a>安裝 BizTalk Adapter Pack 2016
安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]下列兩種方式：  

-   **在互動模式中**： 執行安裝精靈  

-   **以無訊息模式**： 使用命令列  

> [!IMPORTANT]
> - 您必須安裝在電腦上擁有系統管理權限[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，不論您是否要安裝使用精靈或命令列。  
> - 可確定所有[軟體先決條件](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)安裝，才能安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。

## <a name="typical-vs-custom-installation"></a>一般與自訂安裝  
列出安裝類型，以及與每個選項一起安裝的功能：  

- **典型**並**完成**選項會安裝所有的配接器，與相關聯的資料提供者。 您沒有選擇特定的配接器的安裝選項。  

- **自訂**選項會安裝一或多個配接器，與相關聯的資料提供者。 您可以選擇要安裝哪些介面卡。 如果您選擇安裝資料提供者，您也必須安裝對應的介面卡。 不過，您可以安裝配接器，而不需要安裝對應的資料提供者。 執行這項操作，藉由展開**ADO 提供者**節點，然後再選取您不想要安裝的提供者。 請參閱**使用安裝精靈安裝**（在本主題中）。  

   例如，如果您安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，您也必須安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。 不過，您可以安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]而不需要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。  

## <a name="32-bit-and-64-bit-install-scenarios"></a>32 位元和 64 位元安裝案例
 具有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，則[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]適用於： 

- [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計階段 （當產生作業的 LOB 應用程式的中繼資料）

- BizTalk Server 管理主控台設計階段 （用於建立實體連接埠）

  > [!NOTE]
  >  BizTalk Server 管理主控台會以 32 位元的 Microsoft Management Console (MMC) 應用程式執行。  

- BizTalk 執行階段 （傳送和接收訊息時從 LOB 應用程式）

您可以針對所有這些所，使用單一電腦，或使用不同的電腦。 因為這兩[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk MMC 和 32 位元處理序，您必須安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]您用來完成設計階段工作的電腦上。 

### <a name="32-bit-install-scenario"></a>32 位元的安裝案例
在每一部電腦上安裝下列軟體。 如果您使用的在單一電腦，必須在該電腦上安裝所有軟體。 

1. 安裝 32 位元 [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]
2. 安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。
3. 安裝 32 位元 LOB 用戶端，以及其他必要的 Dll。  

### <a name="64-bit-install-scenarios"></a>64 位元的安裝案例

|                                                                                                                 Visual Studio 設計階段                                                                                                                  |                                                                                                                  BizTalk MMC 設計階段                                                                                                                   |                                                                                                                                                                                                                                                                                                         Biztalk 執行階段                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                Visual Studio 設計階段及/或 BizTalk MMC 設計階段 + BizTalk 執行階段                                                                                                                                                                                                                                                                                                                                                                |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。 | 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。 | **32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 64 位元 LOB 用戶端和其他必要的 Dll。 | **32 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> -安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。<br /><br /> **64 位元 BizTalk 處理序**:<br /><br /> 安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。<br /><br /> 安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 64 位元 LOB 用戶端和其他必要的 Dll。<br /><br /> -安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。<br /><br /> -安裝 32 位元 LOB 用戶端和其他必要的 Dll。 |

> [!NOTE]
>  任何在電腦上您要執行設計階段工作，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  

## <a name="install-using-the-setup-wizard"></a>使用安裝精靈安裝  
若要安裝的步驟[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]在互動模式中。  

1. 執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **setup.exe**。  

2. 選取 **安裝 Microsoft BizTalk Adapter**。 在下一步 視窗中，會列出任何遺漏的必要條件程式。 如果遺漏任何，然後選取 程式遺失，並安裝程式會為您安裝它。 

   例如，選取**步驟 2： 安裝 Microsoft BizTalk Adapter Pack**或是**步驟 3： 安裝 Microsoft BizTalk Adapter Pack (x64)**。  

   > [!NOTE]
   >  如果您要安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]虛擬機器上，安裝精靈可能會顯示一則訊息，其所檢查的可用磁碟空間。 如果沒有回應，或只是坐在那裡，就會出現此訊息，則我們建議您**在無訊息模式中安裝**（在本主題中）。  

3. 在 歡迎 畫面中，選取**下一步**。  

4. 接受使用者授權合約 (EULA)，然後按**下一步**。  

5. 在 **選擇 安裝類型**:  

   -   若要安裝的最常見的功能，請選取**典型**。  

   -   若要選取您想要安裝的配接器，請選取**自訂**，然後繼續進行下一個步驟。  

   -   若要安裝所有功能，請選取**完成**。  

       > [!IMPORTANT]
       >  若要安裝您使用與您的企業應用程式，請選取介面卡**自訂**安裝。  

6. **所需**只有當您選擇自訂安裝。 如果您選擇**典型**或是**完成**安裝，然後略過此步驟中，並移至步驟 7。  

    1.  在 **自訂安裝**，展開**基底配接器**若要查看可用的介面卡。  

    2.  您不想為配接器，選取配接器旁的圖示，然後按**整個功能將無法使用**。  

    3.  依序展開**ADO 提供者**，然後選取您不想要安裝的提供者。  

    4.  選取 **[下一步]**。  

7. 選取 [安裝]。  

8. 在 **客戶經驗改進計畫**，您可以選擇註冊。 如果您註冊時，您可以在與 Microsoft 共用的下列資料：  

   - 您安裝所在的電腦硬體的相關資料[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  

   - 資料與企業應用程式版本，您使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  

     [CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699)提供詳細的資訊。  

     選取 [確定]。 

   > [!NOTE]
   >  您一律可以變更此設定執行安裝程式在修復模式下，從**程式**。  

9. 選取 [完成]。  

<a name="BKMK_SilentInst"></a>   
## <a name="install-in-silent-mode"></a>以無訊息模式安裝  
 使用**msiexec**命令來執行無訊息安裝。 隨著 msiexec 命令的詳細資訊，請輸入您想要安裝的個別元件。 下表列出每個元件中的值[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 您可以使用這些值來安裝 （或移除） 特定的元件。 若要安裝 （移除） 多個元件，您可以使用以逗號分隔這些值的組合。  


|                                    元件名稱                                    |                                                                命令列屬性的對應值                                                                 |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]        |                                                                                   DbFeature                                                                                    |
| [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)] |                                                                                OracleEBSFeature                                                                                |
|           [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]           |                                                                             SapBaseAdapterFeature                                                                              |
|        [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]        |                                                                            SiebelBaseAdapterFeature                                                                            |
|            [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]            |                                                                                   SqlFeature                                                                                   |
|        [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]        |     SapAdoFeature<br /><br /> **附註**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]也。      |
|     [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]     | SiebelAdoFeature<br /><br /> **附註**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]也。 |
|                                    所有元件                                    |                                                                                      ALL                                                                                       |

> [!IMPORTANT]
>  功能名稱會區分大小寫。  

 下列步驟會示範如何完成的無訊息安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]為不同的元件。  

### <a name="silent-mode-steps"></a>無訊息模式的步驟

1. 開啟命令提示字元，並移至[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]根中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。  

2. 執行下列命令，根據您想要安裝：  

   > [!NOTE]
   >  若要執行無訊息安裝在 x64 架構的平台上，將`AdaptersSetup.msi`與`AdaptersSetup64.msi`在下列命令。  

   - 若要執行完整安裝，安裝所有包括.NET Framework 資料提供者的介面卡，輸入：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
     ```  

   - 只安裝[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，型別：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
     ```  

   - 只安裝[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，型別：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
     ```  

   - 只安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，型別：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
     ```  

   - 若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]連同[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，型別：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
     ```  

   - 只安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，型別：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
     ```  

   - 若要安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]連同[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，型別：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
     ```  

   - 只安裝[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，型別：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
     ```  

   - 若要安裝的所有基底介面卡，請輸入：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
     ```  

   - 若要安裝兩個.NET Framework 資料提供者，請輸入：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
     ```  

   - 以逗號分隔元件的自訂安裝的任何型別。 例如，若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]具有[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，和[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]類型：  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
     ```  

   - 您也可以選擇加入 ceip 的無訊息安裝的一部分。 類型：  

     ```  
     msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
     ```  

      預設選項是 false。 

     > [!IMPORTANT]
     >  在安裝時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式的評估版，CEIP 的預設選項為 true。  

     如需詳細資訊**msiexec**命令中，輸入`msiexec`上的命令列和按`ENTER`。 或移至[ http://go.microsoft.com/fwlink/p/?LinkId=103199 ](http://go.microsoft.com/fwlink/p/?LinkId=103199)。

## <a name="known-install-issue"></a>已知的安裝問題
安裝相關問題的完整清單，請參閱**疑難排解**主題中的每個介面卡。  

**在 64 位元電腦上的執行安裝程式可能會擲回錯誤時存取結構描述檔案**  

[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式在存取 Microsoft.Adapters 時擲回錯誤。*\<AdapterName\>*_schema.xml 檔案，但配接器安裝會繼續。  

**原因**  

如果 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]已安裝的相同電腦上，目標結構描述所用的檔案都相同。 如此一來，將檔案安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]64 位元安裝程式嘗試存取它時，可能是由 IIS 所使用。  

**解決方式**  

手動複製 Microsoft.Adapters。 *\<AdapterName\>*_schema.xml 檔案*C:\Program Files\Microsoft BizTalk Adapter Pack (x64) \IIS 結構描述*至*C:\Windows\System32\inetsrv\config\schema*。 

## <a name="next-step"></a>下一步
[後續安裝步驟](../adapters-and-accelerators/post-installation-steps-for-biztalk-adapter-pack-2016.md)