# VANET-RMDA-Algorithm
# RMDA algorithm in VANET for maintenance of dynamic clusters
# ======================================================================
# Define options
# ======================================================================
set val(chan)   Channel/WirelessChannel		      ;# channel type
set val(prop)   Propagation/TwoRayGround		      ;# radio-propagation model
set val(netif)  Phy/WirelessPhy		      ;# network interface type
set val(mac)    Mac/802_11		      ;# MAC type
set val(ifq)    Queue/DropTail/PriQueue		      ;# interface queue type
set val(ll)     LL		      ;# link layer type
set val(ant)    Antenna/OmniAntenna		      ;# antenna model
set val(ifqlen) 50		      ;# max packet in ifq
set val(nn)     20	      ;# number of mobilenodes
set val(rp)     AODV		      ;# routing protocol
set opt(x)      652			      ;# x coordinate of topology
set opt(y)      250			     ;# y coordinate of topology
set val(stop)    120.00

# ======================================================================
# Main Program
# ======================================================================
# 
# Initialize Global Variables
# 
set ns_ [new Simulator]

set pdr [open Throughput_Proposed_VS.tr w]
$ns_ trace-all $pdr
set e2e [open EndtoEndDelay_Proposed_VS.tr w]
$ns_ trace-all $e2e
set plr [open PacketLossRatio_Proposed_VS.tr w]
$ns_ trace-all $plr

set tracefd [open vanet1_VS.tr w]
$ns_ trace-all $tracefd

set namtrace [open vanet1_VS.nam w]
$ns_ namtrace-all $namtrace
$ns_ namtrace-all-wireless $namtrace $opt(x) $opt(y)

# set up topography object
set topo    [new Topography]
$topo load_flatgrid $opt(x) $opt(y)

# 
# Create God
# 
create-god $val(nn)
#Nodes to create road structure in NS2
for {set i 5} {$i < $val(nn)} {incr i} {
  set node_($i) [$ns_ node]
  #$node_($i) random-motion 0 ;# disable random motion
}
$node_(5) set X_ -20.0
$node_(5) set Y_ 248
$node_(5) set Z_ 0.0
# $node_(5) setdest 0.5 220 1

$node_(6) set X_ 653.211
$node_(6) set Y_ 246
$node_(6) set Z_ 0.0
# $$node_(6) setdest 615 220 1

$node_(7) set X_ 162
$node_(7) set Y_ 2
$node_(7) set Z_ 0.0
# $$node_(7) setdest 200 1 1

$node_(8) set X_ 457.498
$node_(8) set Y_ 1.9999
$node_(8) set Z_ 0.0
# $$node_(8) setdest 400 1 1

$node_(9) set X_ 225
$node_(9) set Y_ 200
$node_(9) set Z_ 0.0
# $$node_(9) setdest 220 200 1

$node_(10) set X_ 400
$node_(10) set Y_ 200
$node_(10) set Z_ 0.0
# $$node_(10) setdest 400 200 1

$node_(11) set X_ 70
$node_(11) set Y_ 200
$node_(11) set Z_ 0.0
# $$node_(11) setdest 50 188 1

$node_(12) set X_ 195
$node_(12) set Y_ 200
$node_(12) set Z_ 0.0
# $$node_(12) setdest 250 200 1

$node_(13) set X_ 432	
$node_(13) set Y_ 200
$node_(13) set Z_ 0.0
# $$node_(13) setdest 432 200 1

$node_(14) set X_ 567	
$node_(14) set Y_ 200
$node_(14) set Z_ 0.0
# $$node_(14) setdest 577 200 1

$node_(15) set X_ 225	
$node_(15) set Y_ 37
$node_(15) set Z_ 0.0
# $$node_(15) setdest 220 37 1

$node_(16) set X_ 195	
$node_(16) set Y_ 37
$node_(16) set Z_ 0.0
# $$node_(16) setdest 250 37 1

$node_(17) set X_ 400	
$node_(17) set Y_ 37
$node_(17) set Z_ 0.0
# $$node_(17) setdest 400 37 1

$node_(18) set X_ 432	
$node_(18) set Y_ 37
$node_(18) set Z_ 0.0
# $$node_(18) setdest 432 37 1

$node_(19) set X_ 432	
$node_(19) set Y_ 37
$node_(19) set Z_ 0.0
# $$node_(19) setdest 432 37 1
# Configure node

set chan_1_ [new $val(chan)]
$ns_ node-config -adhocRouting  $val(rp) \
                -llType        $val(ll) \
                -macType       $val(mac) \
                -ifqType       $val(ifq) \
                -ifqLen        $val(ifqlen) \
                -antType       $val(ant) \
                -propType      $val(prop) \
                -phyType       $val(netif) \
                -channel       $chan_1_ \
                -topoInstance  $topo \
                -agentTrace    ON \
                -routerTrace   ON \
                -macTrace      ON \
                -movementTrace ON

for {set i 0} {$i < 5} {incr i} {
  set node_($i) [$ns_ node]
  $node_($i) random-motion 0 ;# disable random motion
}
# 
# Provide initial (X,Y, for now Z=0) co-ordinates for mobilenodes
# 
#predefine node in NAM  
  # ID of SUMO: f0_0
$node_(0) set X_ 28.054050937049496
$node_(0) set Y_ 210.05
$node_(0) set Z_ 0.0
$node_(0) setdest 28.054050937049496 210.05 1
  # ID of SUMO: f1_0
$node_(1) set X_ 28.054050937049496
$node_(1) set Y_ 210.05
$node_(1) set Z_ 0.0
$node_(1) setdest 230.65 210.05 1
  # ID of SUMO: f0_1
$node_(2) set X_ 28.054050937049496
$node_(2) set Y_ 210.05
$node_(2) set Z_ 0.0
$node_(2) setdest 28.054050937049496 210.05 1
  # ID of SUMO: f1_1
$node_(3) set X_ 28.054050937049496
$node_(3) set Y_ 210.05
$node_(3) set Z_ 0.0
$node_(3) setdest 230.65 210.05 1
  # ID of SUMO: f0_2
$node_(4) set X_ 28.054050937049496
$node_(4) set Y_ 210.05
$node_(4) set Z_ 0.0
$node_(4) setdest 28.054050937049496 210.05 1


#Edges
$ns_ duplex-link $node_(5) $node_(6) 1Mb 10ms DropTail
$ns_ simplex-link $node_(8) $node_(6) 1Mb 10ms DropTail
$ns_ simplex-link $node_(7) $node_(8) 1Mb 10ms DropTail
$ns_ simplex-link $node_(5) $node_(7) 1Mb 10ms DropTail
$ns_ simplex-link $node_(11) $node_(12) 1Mb 10ms DropTail
$ns_ simplex-link $node_(12) $node_(16) 1Mb 10ms DropTail
$ns_ simplex-link $node_(11) $node_(16) 1Mb 10ms DropTail
$ns_ simplex-link $node_(9) $node_(15) 1Mb 10ms DropTail
$ns_ simplex-link $node_(10) $node_(17) 1Mb 10ms DropTail
$ns_ simplex-link $node_(13) $node_(14) 1Mb 10ms DropTail
$ns_ simplex-link $node_(14) $node_(18) 1Mb 10ms DropTail
$ns_ simplex-link $node_(18) $node_(13) 1Mb 10ms DropTail
$ns_ simplex-link $node_(10) $node_(9) 1Mb 10ms DropTail
$ns_ simplex-link $node_(15) $node_(17) 1Mb 10ms DropTail

for {set i 5} {$i<$val(nn)} {incr i} {
	$node_($i) color white
	$ns_ at 0.0 "$node_($i) color lightgray"
}
set platoon1 [list]
for {set i 0} {$i<5} {incr i} {
	$node_($i) color white
	$ns_ at 0.0 "$node_($i) color black"
	lappend platoon1 $i
}

#1-hop neighbors
for {set i 0} {$i<5} {incr i} {
	set NL($i) [list]
	set x_pos1 [$node_($i) set X_]
	set y_pos1 [$node_($i) set Y_]
	for {set j 0} {$j<5} {incr j} {
		if {$j!=$i} {
			set x_pos2 [$node_($j) set X_]
			set y_pos2 [$node_($j) set Y_]
			set x_pos [expr $x_pos1-$x_pos2]
			set y_pos [expr $y_pos1-$y_pos2]
			set v [expr $x_pos*$x_pos+$y_pos*$y_pos]
			set d [expr sqrt($v)]
			set nd($i,$j) $d
			if {$d<250} {
				$node_($i) add-neighbor $node_($j)
				lappend NL($i) $j
			}
		}
	}
}
# Now produce node movements

proc Distance {x1_v1 y1_v1 x2_v1 y2_v1} {
	set dis [expr sqrt(pow([expr $x2_v1-$x1_v1],2)+ pow([expr $y2_v1-$y1_v1],2))]
	return $dis
}
set dis1 [Distance 28.05 210.05 592.0 210.0]
set dis2 [Distance 592.0 210.0 438.0 23.0]
set dis3 [Distance 438.0 23.0 171.0 24.0]
set dis4 [Distance 171.0 24.0 28.0 210.0]

puts "dis1:$dis1"
for {set i 0} {$i<5} {incr i} {
	set speed($i) 20.0
	set time($i) 0.1
}
set speedv 20.0
set intra_space 50.0

set atime [expr $intra_space/$speedv]
for {set i 0} {$i<5} {incr i} {
	set xp($i) 0
	set yp($i) 0
}
proc varyspeed {} {
	global array names speed
	for {set i1 0} {$i1<5} {incr i1} {
	set speed($i1) 25.0
	}
}
set itc 0

proc NodeMovement {} {
	global itc array names speed dis1 dis2 dis3 dis4 atime array names time ns_ array names node_ array names xp array names yp
	for {set i 0} {$i<5} {incr i} {	
		$ns_ at $time($i) "$node_($i) setdest 592.0 210.0 $speed($i)"
		$ns_ at $time($i) "$node_($i) label $speed($i)"
		set time([expr $i+1]) [expr $time($i)+$atime]
		set dis [expr $speed($i)*$time($i)]
		set xv [$node_($i) set X_]
		set xp($i) $xv
		set yp($i) [$node_($i) set Y_]
		# puts "time([expr $i+1]):$time([expr $i+1])"
	}
	# $ns_ at $time(4) "varyspeed"
	for {set i 0} {$i<5} {incr i} {
		set d1t [expr $dis1/$speed($i)]
		set time($i) [expr $time($i)+$d1t]
		$ns_ at $time($i) "$node_($i) setdest 438.0 23.0 $speed($i)"
	}
	for {set i 0} {$i<5} {incr i} {
		set d2t [expr $dis2/$speed($i)]
		set time($i) [expr $time($i)+$d2t]
		$ns_ at $time($i) "$node_($i) setdest 171.0 23.0 $speed($i)"
	}
	for {set i 0} {$i<5} {incr i} {
		set d3t [expr $dis3/$speed($i)]
		set time($i) [expr $time($i)+$d3t]
		$ns_ at $time($i) "$node_($i) setdest 28.0 210.0 $speed($i)"
	}
	for {set i 0} {$i<5} {incr i} {
		set d4t [expr $dis4/$speed($i)]	
		set time($i) [expr $time($i)+$d4t]
	}
	$ns_ at $time(0) "NodeMovement"
	incr itc
}
# ----------------------
	for {set i 0} {$i<5} {incr i} {	
		$ns_ at $time($i) "$node_($i) setdest 592.0 210.0 $speed($i)"
		$ns_ at $time($i) "$node_($i) label $speed($i)"
		set time([expr $i+1]) [expr $time($i)+$atime]
		set dis [expr $speed($i)*$time($i)]
		set xv [$node_($i) set X_]
		set xp($i) $xv
		set yp($i) [$node_($i) set Y_]
		# puts "time([expr $i+1]):$time([expr $i+1])"
	}
	# $ns_ at $time(4) "varyspeed"
	for {set i 0} {$i<5} {incr i} {
		set d1t [expr $dis1/$speed($i)]
		set time($i) [expr $time($i)+$d1t]
		$ns_ at $time($i) "$node_($i) setdest 438.0 23.0 $speed($i)"
	}
	for {set i 0} {$i<5} {incr i} {
		set d2t [expr $dis2/$speed($i)]
		set time($i) [expr $time($i)+$d2t]
		$ns_ at $time($i) "$node_($i) setdest 171.0 23.0 $speed($i)"
	}
	for {set i 0} {$i<5} {incr i} {
		set d3t [expr $dis3/$speed($i)]
		set time($i) [expr $time($i)+$d3t]
		$ns_ at $time($i) "$node_($i) setdest 28.0 210.0 $speed($i)"
	}
	for {set i 0} {$i<5} {incr i} {
		set d4t [expr $dis4/$speed($i)]	
		set time($i) [expr $time($i)+$d4t]
	}

	for {set i 0} {$i<5} {incr i} {	
		$ns_ at $time($i) "$node_($i) setdest 109.0 210.0 $speed($i)"
		$ns_ at $time($i) "$node_($i) label $speed($i)"
		set time([expr $i+1]) [expr $time($i)+$atime]
		set dis [expr $speed($i)*$time($i)]
		set xv [$node_($i) set X_]
		set xp($i) $xv
		set yp($i) [$node_($i) set Y_]
		# puts "time([expr $i+1]):$time([expr $i+1])"
	}
	set distv [Distance 28.0 210.0 109.0 210.0]
	for {set i 0} {$i<4} {incr i} {
		set d1t [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t]
		$ns_ at $time($i) "$node_($i) setdest 307.0 210.0 22.0"
		$ns_ at $time($i) "$node_($i) label 22.0"
	} 
	set time($i) [expr $time($i)+$d1t]
	$ns_ at $time($i) "$node_($i) setdest 307.0 210.0 19.0"
	$ns_ at $time($i) "$node_($i) label 19.0"
	set distv [Distance 109.0 210.0 307.0 210.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/22.0]
		if {$i==4} {
			set d1t1 [expr $distv/19.0]
		}
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 592.0 210.0 $speed($i)"
		$ns_ at $time($i) "$node_($i) label 25.0"
	} 
	
	set distv [Distance 307.0 210.0 592.0 210.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 438.0 23.0 $speed($i)"
	} 
	
	set distv [Distance 592.0 210.0 438.0 23.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 171.0 23.0 $speed($i)"
	} 
	
	set distv [Distance 438.0 23.0 171.0 23.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 30.0 210.0 $speed($i)"
	} 
	set distv [Distance 171.0 23.0 30.0 210.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 592.0 210.0 $speed($i)"
	} 
	set distv [Distance 30.0 210.0 592.0 210.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 438.0 23.0 $speed($i)"
	} 
	set distv [Distance 592.0 210.0 438.0 23.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 171.0 23.0 $speed($i)"
	} 
	
	set distv [Distance 438.0 23.0 171.0 23.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 30.0 210.0 $speed($i)"
	} 
	set distv [Distance 30.0 210.0 592.0 210.0]
	for {set i 0} {$i<5} {incr i} {
		set d1t1 [expr $distv/$speed($i)]
		set time($i) [expr $time($i)+$d1t1]
		$ns_ at $time($i) "$node_($i) setdest 438.0 23.0 $speed($i)"
	} 

# ----------------------
# 
set atime1 2.5
set dis11(20) [Distance 131.0 210.05 592.0 210.0]
set dis11(21) [Distance 112.0 232.05 592.0 210.0]
set dis11(22) [Distance 70.0 232.05 592.0 210.0]
set dis21 [Distance 592.0 210.0 438.0 23.0]
set dis31 [Distance 438.0 23.0 171.0 24.0]
set dis41 [Distance 171.0 24.0 28.0 210.0]
proc NodeMovement_Disturbance {ditime} {
	global array names speed array names dis11 dis21 dis31 dis41 atime1 ns_ array names node_ array names xp array names yp
	set dtime(20) $ditime
	for {set ni 20} {$ni<=22} {incr ni} {
		# if {$dtime($ni)>83} {
			set speed($ni) 19.9
			$ns_ at $dtime($ni) "$node_($ni) label 25.0"
		# }
		$ns_ at $dtime($ni) "$node_($ni) setdest 592.0 210.0 $speed($ni)"
		set dtime([expr $ni+1]) [expr $dtime($ni)+$atime1]
		set dis [expr $speed($ni)*$dtime($ni)]
		set xv [$node_($ni) set X_]
		set xp($ni) $xv
		set yp($ni) [$node_($ni) set Y_]
	}
	for {set ni 20} {$ni<=22} {incr ni} {
		set d1t [expr $dis11($ni)/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d1t]
		$ns_ at $dtime($ni) "$node_($ni) setdest 438.0 23.0 $speed($ni)"
	}
	
	for {set ni 20} {$ni<=22} {incr ni} {
		set d2t [expr $dis21/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d2t]
		$ns_ at $dtime($ni) "$node_($ni) setdest 171.0 23.0 $speed($ni)"
	}
	for {set ni 20} {$ni<=22} {incr ni} {
		set d3t [expr $dis31/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d3t]
		$ns_ at $dtime($ni) "$node_($ni) setdest 28.0 210.0 $speed($ni)"
	}
	for {set ni 20} {$ni<=22} {incr ni} {
		set d4t [expr $dis41/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d4t]
	}
	set dis11(20) [Distance 28.05 210.05 592.0 210.0]
	set dis11(21) [Distance 28.05 210.05 592.0 210.0]
	set dis11(22) [Distance 28.05 210.05 592.0 210.0]
	set atime1 3.5
	$ns_ at $dtime(20) "NodeMovement_Disturbance $dtime(20)"
}
proc myRand { min max } {
    set maxFactor [expr [expr $max + 1] - $min]
    set value [expr int([expr rand() * 100])]
    set value [expr [expr $value % $maxFactor] + $min]
	return $value
}
set atime2 1.5
set dis12(23) [Distance 554 233 624 231]
set dis12(24) [Distance 513 231 624 231]
set dis12(25) [Distance 466 234 624 231]
set dis12(26) [Distance 420 231 624 231]
set dis12(27) [Distance 383 235 624 231]
set dis12(28) [Distance 344 236 624 231]
set dis12(29) [Distance 304 234 624 231]
set dis12(30) [Distance 255 233 624 231]
set dis12(31) [Distance 217 238 624 231]
set dis12(32) [Distance 174 230 624 231]
set dis22 [Distance 624 231 456.0 16.0]
set dis32 [Distance 456.0 16.0 164.0 15.0]
set dis42 [Distance 164.0 15.0 10.0 240.0]
proc NodeMovement_Disturbance1 {ditime} {
	global array names speed array names dis12 dis22 dis32 dis42 atime2 ns_ array names node_ array names xp array names yp
	set dtime(23) $ditime
	for {set ni 23} {$ni<=32} {incr ni} {
		# if {$dtime($ni)>83} {
			if {$ni==23} {
				set speed($ni) 26
			} else {
				set speed($ni) 25.0
			}
			$ns_ at $dtime($ni) "$node_($ni) label $speed($ni)"
		# }
		$ns_ at $dtime($ni) "$node_($ni) setdest 624 231 $speed($ni)"
		set dtime([expr $ni+1]) [expr $dtime($ni)+$atime2]
		set dis [expr $speed($ni)*$dtime($ni)]
		set xv [$node_($ni) set X_]
		set xp($ni) $xv
		set yp($ni) [$node_($ni) set Y_]
	}
	for {set ni 23} {$ni<=32} {incr ni} {
		set d1t [expr $dis12($ni)/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d1t]
		$ns_ at $dtime($ni) "$node_($ni) setdest 456.0 16.0 $speed($ni)"
	}
	
	for {set ni 23} {$ni<=32} {incr ni} {
		set d2t [expr $dis22/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d2t]
		$ns_ at $dtime($ni) "$node_($ni) setdest 164.0 5.0 $speed($ni)"
	}
	for {set ni 23} {$ni<=32} {incr ni} {
		set d3t [expr $dis32/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d3t]
		$ns_ at $dtime($ni) "$node_($ni) setdest 5.0 240.0 $speed($ni)"
	}
	for {set ni 23} {$ni<=32} {incr ni} {
		set d4t [expr $dis42/$speed($ni)]
		set dtime($ni) [expr $dtime($ni)+$d4t]
	}
	set dis12(23) [Distance 10.0 240.0 624 231]
	set dis12(24) [Distance 10.0 240.0 624 231]
	set dis12(25) [Distance 10.0 240.0 624 231]
	set dis12(26) [Distance 10.0 240.0 624 231]
	set dis12(27) [Distance 10.0 240.0 624 231]
	set dis12(28) [Distance 10.0 240.0 624 231]
	set dis12(29) [Distance 10.0 240.0 624 231]
	set dis12(30) [Distance 10.0 240.0 624 231]
	set dis12(31) [Distance 10.0 240.0 624 231]
	set dis12(32) [Distance 10.0 240.0 624 231]
	set atime2 3.5
	$ns_ at $dtime(23) "NodeMovement_Disturbance1 $dtime(23)"
}

proc attach-cbr-traffic {node sink size interval} {
	global ns_
	set source [new Agent/UDP]
	$source set class_ 2
	$ns_ attach-agent $node $source
	set traffic [new Application/Traffic/CBR]
	$traffic set packetSize_ $size
	$traffic set interval_ $interval
	$traffic attach-agent $source
	$ns_ connect $source $sink
	return $traffic
}
set ti 5.0
set null [new Agent/LossMonitor]
#Beacon Message transmission
proc BeaconMessage {} {
	global array names node_ ns_ ti array names NL null
	for {set i 0} {$i<5} {incr i} {
		foreach nn $NL($i) {
			$ns_ attach-agent $node_($nn) $null
			set cbr [attach-cbr-traffic $node_($i) $null 100 0.05]
			$ns_ at $ti "$cbr start"
			$ns_ at [expr $ti+1.0] "$cbr stop"
		}
		set ti [expr $ti+1.0]
	}
	$ns_ at $ti "BeaconMessage"
}
$ns_ at 5.0 "BeaconMessage"
#platoon1
set head(1) [lindex $platoon1 0]
$ns_ at $ti "$node_($head(1)) label Head"
set lp [llength $platoon1]
set dp1 [expr $lp/2]
set relay(1) [lindex $platoon1 $dp1]
$ns_ at $ti "$node_($relay(1)) label Relay"
set tail(1) [lindex $platoon1 end]
$ns_ at $ti "$node_($tail(1)) label Tail"

set xpv(4) 167.0
set co(1) yellowgreen
set co(2) dodgerblue
set co(3) orange
set co(4) black
set cl(1) [list 4 20 21 22 31 32 3]
set cl(2) [list 1 30 2 29 28 0]
set cl(3) [list 26 25 24 23 27]
set nc 3
proc reclustering {} {
	global array names cl ns_
	set cl(1) [list 4 20 21 22 31 32 3 30]
	set cl(2) [list 1 2 29 28 0]
	set cl(3) [list 26 25 24 23 27]
	$ns_ at [$ns_ now] "CH_Formation"
}
# $ns_ at 101.68 "reclustering"
proc reclustering1 {} {
	global array names cl ns_ nc array names SCH
	set cl(1) [list 4 20 21 22 32 3]
	set cl(2) [list 1 2 29 28 30 31 0]
	set cl(3) [list 26 25 24 27]
	set cl(4) [list 23]
	set nc 4
	set SCH(4) 0
	$ns_ at [$ns_ now] "CH_Formation"
}
$ns_ at 115.65 "reclustering1"
proc reclustering2 {} {
	global array names cl ns_ nc array names SCH
	set cl(1) [list 4 20 21 22 32 3]
	set cl(2) [list 1 2 29 28 30 31 0]
	set cl(3) [list 26 25 24 27]
	set cl(4) [list 23]
	set nc 4
	set SCH(4) 0
	$ns_ at [$ns_ now] "CH_Formation"
}
$ns_ at 118.65 "reclustering2"
for {set i 1} {$i<=$nc} {incr i} {
	set SCH($i) 0
}
set ite 0
#Cluster Head formation
proc CH_Formation {} {
	global ite nc array names SCH array names co array names node_ array names xpv ns_ array names node_ platoon1 array names cl
	
	set sxv 0
	set syv 0
	for {set i 1} {$i<=$nc} {incr i} {
		set m [llength $cl($i)]
		foreach nic $cl($i) {
			if {$nic==4} {
				set xp($nic) $xpv($nic)
				set yp($nic) [$node_($nic) set Y_]
			} else {
				set xp($nic) [$node_($nic) set X_]
				puts "xp($nic):$xp($nic)"
				set yp($nic) [$node_($nic) set Y_]
			}
		}
		foreach nic1 $cl($i) {
			$ns_ at [$ns_ now] "$node_($nic1) add-mark m1 $co($i)"
			$node_($nic1) color $co($i)
			$ns_ at [$ns_ now] "$node_($nic1) color $co($i)"
			set sxv [expr $sxv+$xp($nic1)]
			set syv [expr $syv+$yp($nic1)]
		}
		set xc [expr {wide($sxv/$m)}]
		set yc [expr {wide($syv/$m)}]
		puts "xc:$xc"
		puts "yc:$yc"
		#Relative Distance
		set dislist [list]
		foreach nic2 $cl($i) {
			set iv1 [expr {wide(pow([expr $xp($nic2)-$xc],2))}]
			set iv2 [expr {wide(pow([expr $yp($nic2)-$yc],2))}]
			set iv3 [expr $iv1+$iv2]
			# if {$iv3<0} {
			# set iv3 [expr $iv3*-1]
			# }
			puts "iv1:$iv1"
			puts "iv2:$iv2"
			puts "iv3:$iv3"
			set Rel_Dist($nic2) [expr sqrt($iv3)]
			lappend dislist $Rel_Dist($nic2)
			puts "Rel_Dist($nic2):$Rel_Dist($nic2)"
		}
		set sdl [lsort -real $dislist]
		set max_RD [lindex $sdl end]
		puts "max_RD:$max_RD"
		set alpha 0.6
		set RPML [list]
		foreach nip11 $cl($i) {
			set RPM($nip11) [expr $Rel_Dist($nip11)/$max_RD]
			puts "RPM($nip11):$RPM($nip11)"
			lappend RPML $RPM($nip11)
		}
		set srpm [lsort -real -increasing $RPML]
		puts "srpm:$srpm"
		set min_rpm [lindex $srpm 0]
		puts "min_rpm:$min_rpm"
		if {$ite>0} {
			$ns_ at [$ns_ now] "$node_($SCH($i)) delete-mark m2"
		}
		foreach nip12 $cl($i) {
			if {$min_rpm==$RPM($nip12)} {
				set SCH($i) $nip12
				puts "SCH:$SCH($i)"
			}
		}
		$ns_ at [$ns_ now] "$node_($SCH($i)) add-mark m2 blue square"
	}
	incr ite
}

set chan [new $val(chan)]
$ns_ node-config -adhocRouting  $val(rp) \
                -llType        $val(ll) \
                -macType       $val(mac) \
                -ifqType       $val(ifq) \
                -ifqLen        $val(ifqlen) \
                -antType       $val(ant) \
                -propType      $val(prop) \
                -phyType       $val(netif) \
                -channel       $chan \
                -topoInstance  $topo \
                -agentTrace    ON \
                -routerTrace   ON \
                -macTrace      ON \
                -movementTrace ON
	set node_(20) [$ns_ node]
	$node_(20) set X_ 132
	$node_(20) set Y_ 228
	$node_(20) set Z_ 0
	$node_(20) setdest 132 228 1
	
	set node_(21) [$ns_ node]
	$node_(21) set X_ 112
	$node_(21) set Y_ 232
	$node_(21) set Z_ 0
	$node_(21) setdest 112 232 1
	set node_(22) [$ns_ node]
	$node_(22) set X_ 70
	$node_(22) set Y_ 232
	$node_(22) set Z_ 0
	$node_(22) setdest 70 232 1
	set node_(23) [$ns_ node]
	$node_(23) set X_ 554
	$node_(23) set Y_ 233
	$node_(23) set Z_ 0
	$node_(23) setdest 554 233 1
	set node_(24) [$ns_ node]
	$node_(24) set X_ 513
	$node_(24) set Y_ 231
	$node_(24) set Z_ 0
	$node_(24) setdest 513 231 1
	set node_(25) [$ns_ node]
	$node_(25) set X_ 466
	$node_(25) set Y_ 234
	$node_(25) set Z_ 0
	$node_(25) setdest 466 234 1
	
	set node_(26) [$ns_ node]
	$node_(26) set X_ 420
	$node_(26) set Y_ 231
	$node_(26) set Z_ 0
	$node_(26) setdest 420 231 1
	set node_(27) [$ns_ node]
	$node_(27) set X_ 383
	$node_(27) set Y_ 235
	$node_(27) set Z_ 0
	$node_(27) setdest 383 235 1
	set node_(28) [$ns_ node]
	$node_(28) set X_ 344
	$node_(28) set Y_ 236
	$node_(28) set Z_ 0
	$node_(28) setdest 344 236 1
	
	set node_(29) [$ns_ node]
	$node_(29) set X_ 304
	$node_(29) set Y_ 234
	$node_(29) set Z_ 0
	$node_(29) setdest 304 234 1
	
	set node_(30) [$ns_ node]
	$node_(30) set X_ 255	
	$node_(30) set Y_ 233
	$node_(30) set Z_ 0
	$node_(30) setdest 255 233 1
	set node_(31) [$ns_ node]
	$node_(31) set X_ 217
	$node_(31) set Y_ 238
	$node_(31) set Z_ 0
	$node_(31) setdest 217 238 1
	set node_(32) [$ns_ node]
	$node_(32) set X_ 174
	$node_(32) set Y_ 230
	$node_(32) set Z_ 0
	$node_(32) setdest 174 230 1
	for {set i 20} {$i<=32} {incr i} {
		$node_($i) color whitte
		$ns_ at 0.0 "$node_($i) color whitte"
		set speed($i) 25.0
	}

$ns_ at 78.2 "$node_(20) setdest 131.1 210.05 $speed(20)"
$ns_ at 78.2 "$node_(20) color red"
set x1 [$node_(20) set X_]
set y1 [$node_(20) set Y_]
set mx 132.1
set my 211.2
set dist1m [expr sqrt(pow([expr $mx-$x1],2)+ pow([expr $my-$y1],2))]
set ts [expr $dist1m/$speedv]
puts "ts:$ts"
set ts [expr $ts+78.2]
puts "ts1:$ts"
for {set i 20} {$i<=22} {incr i} {
	$ns_ at $ts "$node_($i) color red"
	$ns_ at $ts "NodeMovement_Disturbance $ts"
}
set mts [expr $ts-7.0]
$ns_ at $mts "NodeMovement_Disturbance1 $mts"
$ns_ at $ts "CH_Formation"
set dly 0
set plrate 0
proc record {} {
	global null ns_ pdr e2e dly plr plrate
	set now [$ns_ now]
	set time 10.0
	set pd [$null set npkts_]
	set pl [$null set nlost_]
	set plrval [expr $pl-$plrate]
	set pdrv [expr $pd/$time]
	set delay [$null set lastPktTime_]
	set ad [expr $delay-$dly]
	set dly $delay
	puts $pdr "$now $pdrv"
	puts $e2e "$now $ad"
	puts $plr "$now $plrval"
	set plrate $pl
	puts "Packets:$pd and delay:$delay"
	$ns_ at [expr $now+$time] "record"
}


proc reduce_speed {nod} {
	global array names speed ns_ array names node_
	set speed($nod) [expr $speed($nod)-15]
	$ns_ at [$ns_ now] "$node_($nod) label $speed($nod)"
	return $speed($nod)
}
$ns_ at 10.0 "record"
#
#===================================
#        Termination        
#===================================
#Define a 'finish' procedure
proc finish {} {
    global ns_ tracefd namtrace
    $ns_ flush-trace
    close $tracefd
    close $namtrace
    exec nam vanet1_VS.nam &
    exit 0
}
for {set i 0} {$i < $val(nn) } { incr i } {
    $ns_ at $val(stop) "\$node_($i) reset"
}
$ns_ at $val(stop) "$ns_ nam-end-wireless $val(stop)"
$ns_ at $val(stop) "finish"
$ns_ at $val(stop) "puts \"done\" ; $ns_ halt"
$ns_ run

