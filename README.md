# VHDL-ControlDoor
 Controlling an entrance door and an exit door for a room that can accommodate up to 15 people.


    library IEEE;
    use IEEE.STD_LOGIC_1164.ALL;
    -------------------------------------------------------------------
    entity control is
   	  port( entBtm , extBtm , inDoorSensor , outDoorSensor , clk , enb , clr: in std_logic );        

    end control;
    -------------------------------------------------------------------
    architecture Behavioral of control is

    signal open_door : std_logic ;   
    signal close_door : std_logic :='1' ;                 
    signal person , counter: integer := 0;


    begin

	   process(clk)
   	begin
	
	   if(clr = '1') then
		   if(enb = '1') then
		   	if(rising_edge(clk)) then
		
			
		     		if(inDoorSensor = '1') then
				      	if(entBtm = '1' and counter < 15 ) then
					       	open_door <= '1' ;
					       	person <= person + 1 ;
						counter <= person ;
					 end if;
					 if(entBtm = '1' and counter = 15 ) then
					       open_door <= '0' ;
				      	end if;	
				     end if;
			
			
				    if(outDoorSensor = '1') then
				      	if(extBtm = '1' and counter > 0) then
						person <= person - 1 ;
						counter <= person ;
						if(counter = 0) then
					    		close_door <= '1' ;
			      		 	else
							null;
						end if;
				     	end if;
		    		    end if;
				
			
		  	end if;
		
	  	 else
	     	 	counter <= person ;
	   	end if;
	else
		counter <= 0 ;
 	end if;
		
 	end process;
    end Behavioral;
    
    
#TestBench

      LIBRARY ieee;
      USE ieee.std_logic_1164.ALL;
    -------------------------------------------------------------------- 
     ENTITY RoomTest IS
     END RoomTest;
    -------------------------------------------------------------------- 
    ARCHITECTURE behavior OF RoomTest IS 
 
    -- Component Declaration for the Unit Under Test (UUT)
 
    COMPONENT control
    PORT(
         entBtm : IN  std_logic;
         extBtm : IN  std_logic;
         inDoorSensor : IN  std_logic;
         outDoorSensor : IN  std_logic;
         clk : IN  std_logic;
         enb : IN  std_logic;
         clr : IN  std_logic
        );
    END COMPONENT;
    

     --Inputs
     signal entBtm : std_logic := '0';
     signal extBtm : std_logic := '0';
     signal inDoorSensor : std_logic := '0';
     signal outDoorSensor : std_logic := '0';
     signal clk : std_logic := '0';
     signal enb : std_logic := '0';
     signal clr : std_logic := '0';

     -- Clock period definitions
      constant clk_period : time := 10 ns;
   
    BEGIN
 
	-- Instantiate the Unit Under Test (UUT)
     uut: control PORT MAP (
          entBtm => entBtm,
          extBtm => extBtm,
          inDoorSensor => inDoorSensor,
          outDoorSensor => outDoorSensor,
          clk => clk,
          enb => enb,
          clr => clr
        );

     -- Clock process definitions
     clk_process :process
     begin
	  	clk <= '0';
  		wait for clk_period/2;
    clk <= '1';
	  	wait for clk_period/2;
    end process;
 
   
     -- Stimulus process
     stim_proc: process
     begin		
            -- hold reset state for 100 ns.
      wait for 100 ns;	
		
		clr <= '0' ;
		wait for 10 ns;
		--reset counter
		
	--------------------------------------------------
		clr <= '1' ;
		enb <= '1' ;
		wait for clk_period/2;
		--16 enetr
		---------------
		inDoorSensor <= '1' ;
	--	wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 1

		inDoorSensor <= '1' ;
	--	wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 2


		inDoorSensor <= '1' ;
	--	wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 3


		inDoorSensor <= '1' ;
	--	wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 4


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 5


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 6


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 7


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 8


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 9


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 10


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 11


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 12


		inDoorSensor <= '1' ;
	--	wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 13


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 14


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 15


		inDoorSensor <= '1' ;
		--wait for clk_period;
		entBtm <= '1' ;
		wait for clk_period;
		inDoorSensor <= '0';
		entBtm <= '0';
		wait for 10 ns;
		--inside_person = 15
		
	----------------------------------------------
		
		--16 exit
		----------
		outDoorSensor <= '1' ;
	--	wait for clk_period;
		extBtm <= '1' ;
		wait for clk_period*2;
		outDoorSensor <= '0';
		extBtm <= '0';
		wait for 10 ns;
		--inside_person = 14
		
		
		outDoorSensor <= '1' ;
	--	wait for clk_period;
		extBtm <= '1' ;
		wait for clk_period*2;
		outDoorSensor <= '0';
		extBtm <= '0';
		wait for 10 ns;
		--inside_person = 13
		
		
		outDoorSensor <= '1' ;
		--wait for clk_period;
		extBtm <= '1' ;
		wait for clk_period*2;
		outDoorSensor <= '0';
		extBtm <= '0';
		wait for 10 ns;
		--inside_person = 12
		
		outDoorSensor <= '1' ;
		--wait for clk_period;
		extBtm <= '1' ;
		wait for clk_period*2;
		outDoorSensor <= '0';
		extBtm <= '0';
		wait for 10 ns;
		
		outDoorSensor <= '1' ;
		--wait for clk_period;
		extBtm <= '1' ;
		wait for clk_period*2;
		outDoorSensor <= '0';
		extBtm <= '0';
		wait for 10 ns;
		

      -- insert stimulus here 


      wait;
     end process;

    END;

